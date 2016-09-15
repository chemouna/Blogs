
# Tips 

## you can put an inner type for functions : 
as in: 
server :: Server ChargeAPI
server = charges
    where
        charges :: TokenInfo -> EitherT ServantErr IO TokenInfo
        charges tokenInfo = do
            liftIO . print $ tokenInfo
            return tokenInfo 
            
