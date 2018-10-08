#!/bin/bash
set -e
set -o pipefail

print-account-list() {
  lpass ls --format "%/as%ag - %an (%au) [%ai]" 2>&1
}

copy-account-field() {
  lpass show --clip "--${2}" "$1" >/dev/null 2>/dev/null
}

open-account-url() {
  local url=$(lpass show --url "$1")
  if [[ -n $url ]]; then
    xdg-open "$url" >/dev/null 2>/dev/null
  else
    exit 2
  fi
}

is-actual-url() {
  local url="$1"
  if [[ -n $url && "$url" != " " && "$url" != "http://" && "$url" != "https://" ]]; then
    return 0
  else
    return 1
  fi
}

show-account-options() {
  local id="$1"

  echo ">> Copy password [$id]"
  echo ">> Copy username [$id]"

  url=$(lpass show --url "$id")
  if is-actual-url "$url"; then
    echo ">> Open $url [$id]"
    echo ">> Copy URL [$id]"
  fi

  echo ">> Copy ID [$id]"
}

is-entry-selected() {
  if [[ -n $@ ]]; then
    return 0
  else
    return 1
  fi
}

id-in-selection() {
  echo "$1" | grep -oE '\[[0-9]+\]$' | tr -d '[]'
}

debug() {
  echo "$@" > /dev/stderr
}

if is-entry-selected "$1"; then
  selected="$1"

  id="$(id-in-selection "$selected")"

  if [[ -n $id ]]; then
    case "$selected" in
      '>> Copy password'*)
        copy-account-field "$id" password ;;
      '>> Copy username'*)
        copy-account-field "$id" username ;;
      '>> Copy URL'*)
        copy-account-field "$id" url ;;
      '>> Copy ID'*)
        copy-account-field "$id" id ;;
      '>> Open'*)
        open-account-url "$id" ;;
      *)
        show-account-options "$id" ;;
    esac
  else
    echo "Could not detect the entry ID of \"${selection}\""
    exit 1
  fi
else
  print-account-list
fi
