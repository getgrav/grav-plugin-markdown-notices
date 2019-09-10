# Grav Markdown Notices Plugin

The **markdown-notices plugin** for [Grav](http://github.com/getgrav/grav) allows generation of notice blocks of text via markdown:

![](assets/screenshot.png)

# Installation

This plugin is easy to install with GPM.

```
$ bin/gpm install markdown-notices
```

# Configuration

Simply copy the `user/plugins/markdown-notices/markdown-notices.yaml` into `user/config/plugins/markdown-notices.yaml` and make your modifications.

```
enabled: true
built_in_css: true
base_classes: 'notices'
level_classes: [yellow, red, blue, green]
```

# Examples

Using one level of `!`

```
! Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris feugiat quam erat, ut iaculis diam posuere nec.
! Vestibulum eu condimentum urna. Vestibulum feugiat odio ut sodales porta. Donec sit amet ante mi. Donec lobortis
! orci dolor. Donec tristique volutpat ultricies. Nullam tempus, enim sit amet fringilla facilisis, ipsum ex
! tincidunt ipsum, vel placerat sem sem vitae risus. Aenean posuere sed purus nec pretium.
```

You will output the following HTML

```
<div class="notices yellow">
    <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Mauris feugiat quam erat, ut iaculis diam posuere nec.
        Vestibulum eu condimentum urna. Vestibulum feugiat odio ut sodales porta. Donec sit amet ante mi. Donec lobortis
        orci dolor. Donec tristique volutpat ultricies. Nullam tempus, enim sit amet fringilla facilisis, ipsum ex
        tincidunt ipsum, vel placerat sem sem vitae risus. Aenean posuere sed purus nec pretium.
    </p>
</div>
```

The `notices` class determined by the `base_classes` and `yellow` class is determined by the `level_classes` in the configuration. You can customize this as you need.

```
!! Lorem ipsum dolor sit amet, **consectetur adipiscing** elit. Mauris feugiat quam erat, ut iaculis diam posuere nec.
!!
!! * List item a
!! * List item b
!!
!! orci dolor. Donec tristique volutpat ultricies. Nullam tempus, enim sit amet fringilla facilisis, ipsum ex
!! tincidunt ipsum, vel placerat sem sem vitae risus. Aenean posuere sed purus nec pretium.
```

Two levels of `!!` will use the second level class etc.  You can also use complex markdown inside the notices.

# Warnings for european users

Since an update to make it able to process the syntax inside a *markdown-table*, the plugin detects any `!` preceeded by a `<space>` as a notice call. Consequently, the european way of adding `<space>` before semicolons or exclamation points or interrogation points lead to trigger the plugin, and to display a notice in place of a link (for example).

So, the next code : 
```
Hello world ! [click me for more information](/page/example).
```
will render "Hello world" followed by a yellow notice displaying the link in raw text (as if markdown wasn't intepreted).

There is no solution nor workaround for now, and the only way is to disable the plugin or to inform the user to stick to american typography standards.


