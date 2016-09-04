
# IO 
IO is a monad, so IO actions can be combined using either the do-notation or the >> and >>= operations from the Monad class.


 do x <- action1
    action2
where 'action1' has type "IO a" and 'action2' has type "IO b", translates into:

 action1 >>= (\x -> action2)
where the second argument of '>>=' has the type "a -> IO b". It's the way the '<-' binding is processed - the name on the left-hand side of '<-' just becomes a parameter of subsequent operations represented as one large IO action. Note



