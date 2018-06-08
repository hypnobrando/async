# async

### Parallel
Makes multiple concurrent functions calls and collects the errors.

```
func UploadAndDownload() error {
  api := Connect()

  var email string
  errs := async.Parallel(
    func() error {
      return api.Post(Request{
        Name: "Brandon",
        Email: "brandoneprice31@gmail.com",
      })
    },

    func() error {
      user, err = api.Get(Request{
        ID: 1234,
      })
      if err != nil {
        return err
      }

      email = user.Email
    },
  )

  if !errs.IsEmpty() {
    return errs.ToError()
  }

  fmt.Println("email:", email)
  return nil
}
```
