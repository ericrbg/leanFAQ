# Lean FAQ
Frequently asked questions about the Lean theorem prover.

## Why does my `def`/`example` time out when the proof is just `sorry`?

Until you get a full proof, change it to a `lemma`. This is a side-effect of Lean's elaborator trying too hard; in a `lemma`, the type is static, but `def`/`example` are both allowed to change it depending on the theorem contents; that is, `lemma x : 1 = 1 := @rfl ℚ 1` will not work, but `example : 1 = 1 : @rfl ℚ 1` will.

## I am trying to use `my_lemma`, but there is also `abc.my_lemma` and `abc` is open. How can I access the non-namespaced `my_lemma`?

Use `_root_.mylemma`.
