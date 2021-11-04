---
layout: post
title: How to fix 'Too many open files' error in RSpec & Capybara?
description: I will walk you through installing Ruby on Rails for development on macOS 10.15 Catalina.
date: 2021-9-6
permalink: how-to-fix-too-many-open-files-rspec-capybara
tags: [ruby-on-rails]
---

### Error:

```
Errno::EMFILE:
       Failed to open TCP connection to 127.0.0.1:9515 (Too many open files - socket(2) for "127.0.0.1" port 9515)
```

After running `ulimit -Sn 10240` in bash, the underlying error becomes visible. For me, this was:

```
 Failure/Error: expect(page).to have_content 'Some text'
       expected to find text "Some text" in "Some other text"
```

---

Ref: https://stackoverflow.com/a/61892983
https://wilsonmar.github.io/maximum-limits/
