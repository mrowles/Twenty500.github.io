Twenty500.github.io
===================

Source repository for Twenty500.com blog using Jekyll

## Installation & Usage
    bundle install
    jekyll serve --watch

_Note: Requires Ruby version 1.9.3 =>. For example use [rbenv](https://github.com/sstephenson/rbenv)_   
    
## Publish to Github Pages
1. Add your domain to _CNAME_
2. Edit your repo address at _Rakefile_
    
Run rake task. **NOTE: It will deploy the generated site to _gh-pages_ branch overwriting it**    
``` 
rake site:publish
```



## Theme Copyright and license

Copyright 2013 Kippt Inc. under [The MIT License ](LICENSE)

