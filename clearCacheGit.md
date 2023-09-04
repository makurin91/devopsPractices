* List git cached `git ls-files --cached`
* Clear cache with .idea `git rm -r --cached .idea`
* Delete DS_Store `find . -name .DS_Store -print0 | xargs -0 git rm -f --ignore-unmatch`