# Bank Application Domain Design

## Domain Objects

### Bounded Contexts
1. **Customer Management Context** - Handles customer information and relationships
2. **Account Management Context** - Manages account creation, maintenance, and closure
3. **Branch Management Context** - Handles branch information
4. **Card Management Context** - Manages ATM card issuance and maintenance

### Aggregates
1. **Customer Aggregate** (Root: Customer)
   - Contains Customer entity and related value objects
2. **Account Aggregate** (Root: Account)
   - Contains Account (Savings/Current) and related value objects
3. **Branch Aggregate** (Root: Branch)
   - Contains Branch entity
4. **ATMCard Aggregate** (Root: ATMCard)
   - Contains ATMCard entity

### Entities
1. **Customer**
   - ID (String)
   - Name (String)
   - AccountNumbers (List<String>)
2. **Account** (Abstract Base)
   - AccountNumber (String)
   - AccountType (Enum: SAVINGS/CURRENT)
   - BranchName (String)
   - Balance (Decimal)
3. **SavingsAccount** (extends Account)
   - MinimumBalance (Decimal)
4. **CurrentAccount** (extends Account)
   - LinkedSavingAccountNumber (String)
5. **Branch**
   - BranchName (String)
6. **ATMCard**
   - ID (String)
   - DateOfIssue (Date)

### Value Objects
1. **Address**
   - Street (String)
   - City (String)
   - State (String)
   - PostalCode (String)
   - Country (String)
2. **EmploymentDetails**
   - CompanyName (String)
   - TelephoneNo (String)
   - AnnualSalaryRange (String)
   - Occupation (String)
   - Designation (String)
3. **AccountHolder**
   - HolderID (String)
   - JointHolderID (String) [Optional]

## Relationships

1. **Customer to Account**:
   - One-to-Many (1 Customer can have 0..* Accounts)
   - Customer maintains list of account numbers
   - Account references customer via HolderID

2. **Account to Branch**:
   - Many-to-One (Many Accounts can belong to 1 Branch)
   - Account references Branch via BranchName
   - Branch has no direct reference to Accounts

3. **Customer to ATMCard**:
   - One-to-One (1 Customer can have 0..1 ATMCard)
   - ATMCard references Customer via CustomerID

4. **Account Inheritance**:
   - SavingsAccount and CurrentAccount inherit from Account
   - CurrentAccount can link to one SavingsAccount

5. **Joint Account Relationship**:
   - Account can have 1-2 holders (via HolderID and JointHolderID)
   - JointHolderID is optional

## Domain Model Diagram

```plantuml
@startuml BankDomainModel

' Enable DDD stereotypes
skinparam dddBoundaryColor #6699cc
skinparam dddControlColor #88cc88
skinparam dddEntityColor #ffaa88
skinparam dddValueObjectColor #ffcc66

package "Customer Management" {
  entity Customer {
    + String ID <<identity>>
    + String Name
    + List<String> AccountNumbers
  }
  
  valueObject Address {
    + String Street
    + String City
    + String State
    + String PostalCode
    + String Country
  }
  
  valueObject EmploymentDetails {
    + String CompanyName
    + String TelephoneNo
    + String AnnualSalaryRange
    + String Occupation
    + String Designation
  }
  
  Customer "1" *-- "1" Address
  Customer "1" *-- "1" EmploymentDetails
}

package "Account Management" {
  abstract entity Account <<abstract>> {
    + String AccountNumber <<identity>>
    + AccountType Type
    + String BranchName
    + Decimal Balance
  }
  
  entity SavingsAccount {
    + Decimal MinimumBalance
  }
  
  entity CurrentAccount {
    + String LinkedSavingAccountNumber
  }
  
  Account <|-- SavingsAccount
  Account <|-- CurrentAccount
  
  valueObject AccountHolder {
    + String HolderID
    + String JointHolderID
  }
  
  Account "1" *-- "1" AccountHolder
}

package "Branch Management" {
  entity Branch {
    + String BranchName <<identity>>
    + String Address
  }
}

package "Card Management" {
  entity ATMCard {
    + String ID <<identity>>
    + Date DateOfIssue
  }
}

' Relationships between aggregates
Customer "1" <- "0..*" Account : holds >
Customer "1" <- "0..1" ATMCard : has >
Account "0..*" -> "1" Branch : belongs to >
CurrentAccount "0..1" -> "1" SavingsAccount : links to >

' Joint account relationship note
note top of AccountHolder
  HolderID references Customer.ID
  JointHolderID (optional) references another Customer.ID
end note

@enduml