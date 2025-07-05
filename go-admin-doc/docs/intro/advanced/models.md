
---

models mainly interact with the database.

## package and import

First, set the `package` name and import the required packages.

```go
package models

import (
	"go-admin/common/models"
)
```

## Table struct

```go
type SysPost struct {
	PostId   int    `gorm:"primaryKey;autoIncrement" json:"postId"` // Post ID
	PostName string `gorm:"size:128;" json:"postName"`              // Post name
	PostCode string `gorm:"size:128;" json:"postCode"`              // Post code
	Sort     int    `gorm:"size:4;" json:"sort"`                    // Sort order
	Status   int    `gorm:"size:4;" json:"status"`                  // Status
	Remark   string `gorm:"size:255;" json:"remark"`                // Description
	models.ControlBy
	models.ModelTime

	DataScope string `gorm:"-" json:"dataScope"`
	Params    string `gorm:"-" json:"params"`
}

func (SysPost) TableName() string {
	return "sys_post"
}

func (e *SysPost) Generate() models.ActiveRecord {
	o := *e
	return &o
}

func (e *SysPost) GetId() interface{} {
	return e.PostId
}
```
Where to get help:

If you have any questions while reading this tutorial, you can visit Submit Suggestions. https://github.com/go-admin-team/go-admin/issues/new