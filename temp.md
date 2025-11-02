


## Budget Categories with Cascade Foreign Key

CREATE TABLE dbo.BudgetCategory (
    CategoryID       INT IDENTITY(1,1) NOT NULL PRIMARY KEY,
    ParentCategoryID INT NULL REFERENCES dbo.BudgetCategory(CategoryID),
    Code             VARCHAR(12) NOT NULL UNIQUE,
    Name             VARCHAR(100) NOT NULL,
    IsIncome         BIT NOT NULL DEFAULT 0,
    IsTransfer       BIT NOT NULL DEFAULT 0,
    IsFixed          BIT NOT NULL DEFAULT 0,
    SortOrder        INT NOT NULL DEFAULT 0,
    IsActive         BIT NOT NULL DEFAULT 1
);
GO

ALTER TABLE dbo.BudgetCategory
  ADD CONSTRAINT FK_BudgetCategory_Parent
  FOREIGN KEY (ParentCategoryID)
  REFERENCES dbo.BudgetCategory(CategoryID)
  ON DELETE SET NULL;
GO