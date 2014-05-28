README
======

This is a sphinx-doc setup for github.io.

The sources are in `docs` and the build directory is at the top.
If you want to start your own sphinx-blog, clone this, and start
from the `clean-blog` branch (which is minimally setup).

Operation
---------

```
cd docs
make html
```

Then simply git commit (including the generated results) and push
to your  MyName.github.io repository (which renders from master, 
whereas project repositories render from gh-pages branch).
Be sure that you have a `.nojekyll` file, so that the results
render properly.


