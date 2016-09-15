
# HSpec 

hspec : Run given spec and write a report to stdout. Exit with exitFailure if at least one spec item fails.

### describe :: String -> SpecWith a -> SpecWith a -- Test.Hspec
The describe function combines a list of specs into a larger spec. 
#### TODO: look more into impl of describe as it could server as an example of how to create functions that enable nesting 
    // maybe its since SpecWith uses SpecM it just is a combination of monads 
     
### it :: (?loc :: CallStack, Example a) => String -> a -> SpecWith (Arg a)
The it function creates a spec item, consists of:
 - a textual description of a desired behavior
 - an example for that behavior
describe "absolute" $ do
  it "returns a positive number when given a negative number" $
    absolute (-1) == 1

### pending :: Expectation
pending can be used to indicate that an example is pending.
If you want to textually specify a behavior but do not have an example yet 
-> Use this to describe all uses cases to implement later 
#### TODO: look more into the general idea of adding constructs that allow dev to write only part of 
      the implementation & fill in rest later : like this pending, haskell undefined, idris holes ... 
       -> does clojure have one ? (a fn that return nil ?)
       
### before :: IO a -> SpecWith a -> Spec
Run a custom action before every spec item. 
like @Before in junit 

### beforeAll :: IO a -> SpecWith a -> Spec
Run a custom action before the first spec item 
like @BeforeClass in junit 

### Qs
- why does hspec have many aliases like context for describe and specify for it 


## Testing with Snap 

### snap :: Handler b b () -> SnapletInit b b -> SpecWith (SnapHspecState b) -> Spec  -- in Test.Hspec.Snap
 The way to run a block of SnapHspecM tests within an hspec test suite. This takes 
both the top level handler (usually `route routes`, where routes are all the routes for your site) 
and the site initializer (often named app), and a block of tests. 
A test suite can have multiple calls to snap, though each one will cause the site initializer to run, 
which is often a slow operation (and will slow down test suites).


### type SnapHspecM b = StateT (SnapHspecState b) IO -- in Test.Hspec.Snap
The main monad that tests run inside of. This allows both access to the application 
 (via requests and eval) and to running assertions (like should404 or shouldHaveText).

### type SpecWith a = SpecM a () -- in Test.Hspec
(i think it's just general construct to test monadic stuff)

### data SnapHspecState b  -- in Test.Hspec.Snap
Internal state used to share site initialization across tests, and to propogate failures. 
it contains : 
Result
Main handler
Startup state
Startup state
Session state
Before handler (runs before each eval)
After handler (runs after each eval). 

type Spec = SpecWith ()

### newtype StateT s m a :: * -> (* -> *) -> * -> *  -- in mtl
A state transformer monad parameterized by:
s - The state.
m - The inner monad.
The return function leaves the state unchanged, while >>= uses the final state of the first computation as the initial state of the second.

### data Handler b v a  -- in Snap
Snaplet infrastructure is available during runtime request processing through the Handler monad. 
There aren't very many standalone functions to read about here, but this is deceptive. The key 
is in the type class instances. Handler is an instance of MonadSnap, which means it is the monad 
you will use to write all your application routes. It also has a MonadSnaplet instance, 
which gives you all the functionality described above.

### data SnapletInit b v Source
Opaque newtype which gives us compile-time guarantees that the user is using makeSnaplet and either nestSnaplet or embedSnaplet correctly.
#### TODO: this is an interesting pattern to use a type for compile time guarantees that some methods are called correctly -> How ? 

-> should404

### setResult :: Result -> SnapHspecM b () Source #
Records a test Success or Fail. Only the first Fail will be recorded (and will cause the whole block to Fail). 

