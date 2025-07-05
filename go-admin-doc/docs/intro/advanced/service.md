---

```yaml
nav: Development
group:
  title: Advanced
  order: 2
title: service
toc: content
```

---

## import

```go
package service

import (
	"errors"

	"github.com/go-admin-team/go-admin-core/sdk/service"
	"gorm.io/gorm"

	"go-admin/app/admin/models"
	"go-admin/app/admin/service/dto"
	cDto "go-admin/common/dto"
)
```

## Define Business Object Struct

```go
type SysPost struct {
	service.Service
}
```

## GetList

`GetList` handles business logic for paginated list queries, using related dto and models functions.

Example function:

```go
// GetPage fetches a paginated list of SysPost
func (e *SysPost) GetPage(c *dto.SysPostPageReq, list *[]models.SysPost, count *int64) error {
	var err error
	var data models.SysPost

	err = e.Orm.Model(&data).
		Scopes(
			cDto.MakeCondition(c.GetNeedSearch()),
			cDto.Paginate(c.GetPageSize(), c.GetPageIndex()),
		).
		Find(list).Limit(-1).Offset(-1).
		Count(count).Error
	if err != nil {
		e.Log.Errorf("db error:%s \r", err)
		return err
	}
	return nil
}
```

## Get

`Get` handles business logic for fetching a single record by ID, using related dto and models functions.

Example function:

```go
// Get fetches a SysPost object by ID
func (e *SysPost) Get(d *dto.SysPostGetReq, model *models.SysPost) error {
	var err error
	var data models.SysPost

	db := e.Orm.Model(&data).
		First(model, d.GetId())
	err = db.Error
	if err != nil && errors.Is(err, gorm.ErrRecordNotFound) {
		err = errors.New("Object not found or no permission to view")
		e.Log.Errorf("db error:%s", err)
		return err
	}
	if db.Error != nil {
		e.Log.Errorf("db error:%s", err)
		return err
	}
	return nil
}
```

## Post

`Post` handles business logic for creating a single record, using related dto and models functions.

Example function:

```go
// Insert creates a new SysPost record
func (e *SysPost) Insert(c *dto.SysPostInsertReq) error {
	var err error
	var data models.SysPost
	c.Generate(&data)
	err = e.Orm.Create(&data).Error
	if err != nil {
		e.Log.Errorf("db error:%s", err)
		return err
	}
	return nil
}
```

## Put

`Put` handles business logic for updating a single record, using related dto and models functions.

Example function:

```go
// Update modifies an existing SysPost record
func (e *SysPost) Update(c *dto.SysPostUpdateReq) error {
	var err error
	var model = models.SysPost{}
	e.Orm.First(&model, c.GetId())
	c.Generate(&model)

	db := e.Orm.Save(&model)
	if db.Error != nil {
		e.Log.Errorf("db error:%s", err)
		return err
	}
	if db.RowsAffected == 0 {
		return errors.New("No permission to update this data")
	}
	return nil
}
```

## Delete

`Delete` handles business logic for deleting a single record, using related dto and models functions.

Example function:

```go
// Remove deletes a SysPost record
func (e *SysPost) Remove(d *dto.SysPostDeleteReq) error {
	var err error
	var data models.SysPost

	db := e.Orm.Model(&data).Delete(&data, d.GetId())
	if db.Error != nil {
		err = db.Error
		e.Log.Errorf("Delete error: %s", err)
		return err
	}
	if db.RowsAffected == 0 {
		err = errors.New("No permission to delete this data")
		return err
	}
	return nil
}
```
