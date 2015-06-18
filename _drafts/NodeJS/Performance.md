## Test performance
Kiểm tra thời gian từ lúc bắt đầu đến khi kết thúc một tác vự

    console.time('xx'); ---> console.timeEnd('xx');
    
Example

    app.get('/auth', function (req, res, next) {
      console.time('xx');
      authViaToken(req, res).then(function(user) {
        req.user = user;
      })
      .then(function () {
        if (req.user.level < 1) {
          throw new Error("Can't authenticate");
        }
      })
      .finally(function() {
        next();
        console.timeEnd('xx');
      })
      .catch(function (err) {
        return res.status(403).json(err.message);
      });
    }, City.findAll);