# nix-dotfiles

note on active files (e.g. JS8Call.ini):
  JS8Call modifies it's .ini with state information every run. This causes git havoc. To deal with this we will:

git update-index --skip-worktree JS8Call.ini

which causes git to not track these changes in its state. 

If we make an actual configuration change, we will:

# 1. Temporarily pull the file back into git tracking
git update-index --no-skip-worktree JS8Call.ini

# 2. Review and stage only your intended change
git add -p JS8Call.ini
git commit -m "radio: update js8call macros"

# 3. Lock it back down
git update-index --skip-worktree JS8Call.ini

