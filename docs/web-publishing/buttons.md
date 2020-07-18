---
layout: default
title: Buttons
parent: Web Publishing
nav_order: 2
---

# Buttons
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc .contents-list}

---

## 비교

### Bootstrap
{:.bigger}

##### Button styles
{:.bigger }

<div class="sample-box" markdown="1">
  <button type="button" class="btn btn-primary">Primary</button>
  <button type="button" class="btn btn-danger">Danger</button>
  <button type="button" class="btn btn-link">Link</button>
  <button type="button" class="btn btn-outline-primary">Primary</button>
</div>


```html
<button type="button" class="btn btn-primary">Primary</button>
<button type="button" class="btn btn-secondary">Secondary</button>
<button type="button" class="btn btn-success">Success</button>
<button type="button" class="btn btn-danger">Danger</button>
<button type="button" class="btn btn-warning">Warning</button>
<button type="button" class="btn btn-info">Info</button>
<button type="button" class="btn btn-light">Light</button>
<button type="button" class="btn btn-dark">Dark</button>
<button type="button" class="btn btn-link">Link</button>
<!--Outline buttons-->
<button type="button" class="btn btn-outline-primary">Primary</button>
```


##### Button Tag
{:.bigger }

<div class="sample-box" markdown="1">
<input class="btn btn-primary" type="button" value="Input">
<button class="btn btn-primary" type="submit">Button</button>
</div>

```html
<a class="btn btn-primary" href="#" role="button">Link</a>
<button class="btn btn-primary" type="submit">Button</button>
<input class="btn btn-primary" type="button" value="Input">
<input class="btn btn-primary" type="submit" value="Submit">
<input class="btn btn-primary" type="reset" value="Reset">
```



##### Button Size
{:.bigger }

<div class="sample-box" markdown="1">
<p><button type="button" class="btn btn-primary btn-lg">Large button</button></p>
<p><button type="button" class="btn btn-primary btn-sm">Small button</button></p>
<p><button type="button" class="btn btn-primary btn-lg btn-block">Block level button</button></p>
</div>

```html
<button type="button" class="btn btn-primary btn-lg">Large button</button>
<button type="button" class="btn btn-primary btn-sm">Small button</button>
<button type="button" class="btn btn-primary btn-lg btn-block">Block level button</button>
```

---


### JustTheDocs
{:.bigger}

##### Button styles
{:.bigger }

<div class="code-example" markdown="1">
[Link button](http://url/){: .btn }
<button type="button" name="button" class="btn">Button</button>
{:.flex}
</div>

```html
  <a href="http://url/" class="btn">button</a>
  <button type="button" name="button" class="btn">Button</button>
```

<div class="code-example" markdown="1">
[Link button](http://url/){: .btn .btn-purple }
<button type="button" name="button" class="btn btn-blue mr-2">Button</button>
{:.flex}
</div>

```html
<a href="http://url/" class="btn btn-purple">button</a>
<button type="button" name="button" class="btn btn-purple">Button</button>
```

<div class="code-example" markdown="1">
[Link button](http://url/){: .btn .btn-outline }
<button type="button" name="button" class="btn btn-outline">Button</button>
{:.flex}
</div>

```html
<a href="http://url/" class="btn btn-outline">button</a>
<button type="button" name="button" class="btn btn-outline">Button</button>
```


##### Button Size 
{:.bigger }

<div class="code-example" markdown="1">
<span class="fs-6">[Button size](http://url/){: .btn }</span>
<span class="fs-4">[Button size](http://url/){: .btn }</span>
{:.flex}
</div>

```html
  <span class="fs-6"><button type="button" name="button" class="btn">Button</button></span>
  <span class="fs-6"><a href="http://url/" class="btn">Button size</a></span>
  <span class="fs-5"><a href="http://url/" class="btn btn-purple">Button size</a></span>
  <span class="fs-4"><a href="http://url/" class="btn btn-outline">Button size</a></span>
  <span class="fs-2"><a href="http://url/" class="btn">Button size</a></span>
```


##### Button with space
{:.bigger }

<div class="code-example" markdown="1">
[Button with space](http://url/){: .btn .btn-purple .mr-2 }
<button type="button" name="button" class="btn btn-purple mr-8">Button</button>
<button type="button" name="button" class="btn btn-blue mr-4">Button</button>
{:.flex}
</div>

```html
<a href="http://url/" class="btn btn-purple  mr-2">button</a>
<button type="button" name="button" class="btn btn-purple mr-8">Button</button>
```


---

## 참고링크
- [Bootstrap Buttons](https://getbootstrap.com/docs/4.1/components/buttons/){:target="_blank"}
