
# kaggle

Built using:

    cabal init  --non-interactive kaggle -d "base,dataframe,perf,chart-svg,prettychart"

Run in ghci using:

    import Prelude
    :set -XImportQualifiedPost
    :set -Wno-type-defaults
    :set -Wno-name-shadowing
    :set -XOverloadedLabels
    :set -XOverloadedStrings
    :set -XTupleSections
    :set -XQuasiQuotes
    import Control.Category ((>>>))
    import Data.Function
    import Data.Maybe
    import Data.Bool
    import Data.List qualified as List
    import Control.Monad
    import Data.Bifunctor
    import Chart
    import Prettychart
    import Chart.Examples
    import Optics.Core hiding ((|>))
    import Perf
    import Data.ByteString.Char8 qualified as C
    import Data.Text qualified as T
    import Prettyprinter
    (display, quit) <- startChartServer (Just "kaggle")
    disp x = display $ x & set (#markupOptions % #markupHeight) (Just 250) & set (#hudOptions % #frames % ix 1 % #item % #buffer) 0.1

    Configuration is affected by the following files:
    - cabal.project
    Build profile: -w ghc-9.12.2 -O1
    In order, the following will be built (use -v for more details):
     - kaggle-0.1.0.0 (interactive) (lib) (first run)
    Preprocessing library for kaggle-0.1.0.0...
    GHCi, version 9.12.2: https://www.haskell.org/ghc/  :? for help
    [1 of 1] Compiling Kaggle           ( src/Kaggle.hs, interpreted )
    src/Kaggle.hs:3:1: warning: [GHC-66111] [-Wunused-imports]
        The import of ‘DataFrame’ is redundant
          except perhaps to import instances from ‘DataFrame’
        To import instances alone, use: import DataFrame()
      |
    3 | import DataFrame
      | ^^^^^^^^^^^^^^^^
    
    src/Kaggle.hs:4:1: warning: [GHC-66111] [-Wunused-imports]
        The import of ‘Chart’ is redundant
          except perhaps to import instances from ‘Chart’
        To import instances alone, use: import Chart()
      |
    4 | import Chart
      | ^^^^^^^^^^^^
    
    src/Kaggle.hs:6:1: warning: [GHC-66111] [-Wunused-imports]
        The import of ‘Prettychart’ is redundant
          except perhaps to import instances from ‘Prettychart’
        To import instances alone, use: import Prettychart()
      |
    6 | import Prettychart
      | ^^^^^^^^^^^^^^^^^^
    
    Ok, one module loaded.
    Setting phasers to stun... (port 9160) g(hcctir>l -c to quit)

    disp lineExample

    True

It&rsquo;s a good chunky first example.

    s <- readFile "other/test.csv"
    length s

    23021430

    rf = readFile "other/test.csv"
    (m,n) <- tickIO (length <$> rf)
    print n
    toSecs m

    23021430
    0.144087667

