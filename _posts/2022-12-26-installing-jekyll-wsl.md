---
layout: post
title:  "Installing Jekyll on Windows Subsystem for Linux"
date:   2022-12-26 17:15:00 -0500
category: guide
---

### [Install Windows Subsystem for Linux](https://apps.microsoft.com/store/detail/windows-subsystem-for-linux/9P9TQF7MRM4R)

### [Install Ubuntu](https://apps.microsoft.com/store/detail/ubuntu/9PDXGNCFSCZV)

### Install Dependencies

- Start Ubuntu
- `sudo apt-get update -y && sudo apt-get upgrade -y`
- `sudo apt-get install ruby-full build-essential dh-autoreconf -y`
- Add the following with `nano ~/.bashrc`

{% highlight sh%}
# Ruby exports
export GEM_HOME=\$HOME/gems
export PATH=\$PATH:\$HOME/gems/bin
{% endhighlight %}

- `gem update`
- `gem install jekyll bundler`
- Check that Jekyll is installed with `jekyll -v`

### Official Jekyll Docs

- [Step-by-Step Guide](https://jekyllrb.com/docs/step-by-step/01-setup/)
- [Install for Windows](https://jekyllrb.com/docs/installation/windows/)
