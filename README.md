```haskell
module Ashura where

data SocialNetwork = GitHub [Char]
data User = User [Char] Int [[Char]] [[Char]] [SocialNetwork] [[Char]]

instance Show SocialNetwork where
  show (GitHub username) = "github.com/" ++ username

instance Show User where
  show (User name age languages games socialNetworks wantToLearn) = "Olá, meu nome é " 
    ++ name
    ++ ", tenho " 
    ++ show age 
    ++ ", utilizo com " 
    ++ intercalate languages 
    ++ ", gosto de " 
    ++ intercalate games
    ++ ", minhas redes sociais são "
    ++ intercalate (map show socialNetworks)
    ++ " e gostaria de aprender "
    ++ intercalate wantToLearn
    ++ "."

intercalate :: [String] -> String
intercalate [] = []
intercalate [x] = x
intercalate [x, y] = x ++ " e " ++ y
intercalate (x:xs) = x ++ ", " ++ intercalate xs

ashura = User "joaozinho quarentena e nove / ashura" 16 ["PHP", "JavaScript", "Haskell"] ["Minecraft"] [GitHub "ashuradev"] ["Ruby"]

main = print ashura
```
`runhaskell ./Ashura.hs`

Olá, meu nome é joaozinho quarentena e nove / ashura, tenho 16, utilizo com PHP, JavaScript e Haskell, gosto de Minecraft, minhas redes sociais são github.com/ashuradev e gostaria de aprender Ruby.
