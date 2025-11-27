
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
    import DataFrame as D
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

    Setting phasers to stun... (porgth c9i1>6 0) (ctrl-c to quit)

    disp lineExample

    True

It&rsquo;s a good chunky first example.

file read:

    s <- readFile "other/test.csv"
    length s

    23021430

    rf = readFile "other/test.csv"
    (m,n) <- tickIO (length <$> rf)
    print n
    toSecs m

    23021430
    0.144087667


## dataframe readCsv

    (m,df) <- tickIO (D.readCsv "other/test.csv")
    print $ toSecs m
    :t df

    0.944859458
    df :: DataFrame

    describeColumns df

    -----------------------------------------------------------------
        Column Name      | # Non-null Values | # Null Values |  Type
    ---------------------|-------------------|---------------|-------
            Text         |        Int        |      Int      |  Text
    ---------------------|-------------------|---------------|-------
    grade_subgrade       | 254569            | 0             | Text
    loan_purpose         | 254569            | 0             | Text
    employment_status    | 254569            | 0             | Text
    education_level      | 254569            | 0             | Text
    marital_status       | 254569            | 0             | Text
    gender               | 254569            | 0             | Text
    interest_rate        | 254569            | 0             | Double
    loan_amount          | 254569            | 0             | Double
    credit_score         | 254569            | 0             | Int
    debt_to_income_ratio | 254569            | 0             | Double
    annual_income        | 254569            | 0             | Double
    id                   | 254569            | 0             | Int

