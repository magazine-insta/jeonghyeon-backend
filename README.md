# π₯¨ jeonghyeon-backend-magazine π₯¨
http://13.209.40.211/

μμ CORS μ΄μ΄λ μ£Όμ: http://localhost:3000

## API List

## 1. κ²μκΈ μμ±
  βοΈ Method: POST
  
  βοΈ Api: /api/post
  
  βοΈ Request: 
  
              {String "imageUrl":"imageUrl" ,
  
              String "contents":"contents", 
              
              String "layoutType":"layoutType"}    (DEFAULT, LEFT, RIGHT)
              
  βοΈ Response: Long μ μ₯ν postId
              
              // λ‘κ·ΈμΈνμ§ μμ μ¬μ©μμ κ²½μ° 400μλ¬μ λ©μμ§("λ‘κ·ΈμΈνμ§ μμ μ¬μ©μλ ν¬μ€νν  μ μμ΅λλ€.")
              // layoutTypeμ μ°μ  (DEFAULT, LEFT, RIGHT) μ€ νλλ‘ μ€μ λμ΄ μμ΅λλ€. κ·Έ μΈ λ¬Έμμ΄ μλ ₯μ 400μλ¬κ° λμ΅λλ€.
              
## 2. λ¨μΌ κ²μκΈ μ‘°ν              
  βοΈ Method: GET
  
  βοΈ Api: /api/post/{postId}
  
  βοΈ Request: Long postId
  
  βοΈ Response: 
                          
              PostToFE = {Long "postId": "postId",                  (PostToFE: νλ‘ νΈμλλ‘ λ³΄λ΄κΈ° μν΄ μ¬κ΅¬μ±ν Postμ λ³΄λͺ¨μν΄λμ€)
  
                          String "nickname": "nickname",
                          
                          String "createdAt": "createdAt",
                          
                          String "contents": "contents",
                          
                          String "imageUrl": "imageUrl",
                          
                          Long "likeCnt": "likeCnt",
                          
                          Boolean "userLiked"; "userLiked"          (νμ¬ λ‘κ·ΈμΈν μ¬μ©μκ° ν΄λΉ κ²μκΈμ μ’μμνλμ§ μ¬λΆ ex. true, false)
                          
                          String "layoutType"; "layoutType"}        (DEFAULT, LEFT, RIGHT)
              
## 3. μ μ²΄ κ²μκΈ μ‘°ν
  βοΈ Method: GET
  
  βοΈ Api: /api/post
  
  βοΈ Request: μμ λλ νμ΄μ§μ μν κ²½λ‘λ³μ (ex. /api/post?page=0&size=3)
  
  βοΈ Response: PostToFE μ List 
  
  
## 4. κ²μκΈ μμ 
  βοΈ Method: PUT
  
  βοΈ Api: /api/post/{postId}
  
  βοΈ Request: 
            
             {String "imageUrl": "imageUrl" ,
  
              String "contents": "contents", 
  
              String "layoutType": "layoutType"}   (DEFAULT, LEFT, RIGHT)
  
  βοΈ Response: Long μμ ν postId
  
              // λ‘κ·ΈμΈνμ§ μμ μ¬μ©μμ κ²½μ° 400μλ¬μ λ©μμ§("λ‘κ·ΈμΈμ΄ νμν©λλ€.")
              // μμ±μκ° μλ μ¬μ©μμ κ²½μ° 400μλ¬μ λ©μμ§("μμ±μκ° μλλ©΄ μμ ν  μ μμ΅λλ€.")
  
## 5. κ²μκΈ μ­μ 
  βοΈ Method: DELETE
  
  βοΈ Api: /api/post/{postId}/like
  
  βοΈ Request: Long postId
  
  βοΈ Response: String μ­μ ν κ²μκΈμ imageUrl
  
               // λ‘κ·ΈμΈνμ§ μμ μ¬μ©μμ κ²½μ° 400μλ¬μ λ©μμ§("λ‘κ·ΈμΈμ΄ νμν©λλ€.")
               // μμ±μκ° μλ μ¬μ©μμ κ²½μ° 400μλ¬μ λ©μμ§("μμ±μκ° μλλ©΄ μ­μ ν  μ μμ΅λλ€.")
  
## 6. μ’μμ λ³ν
  βοΈ Method: GET
  
  βοΈ Api: /api/post/{postId}/like
  
  βοΈ Request: Long postId
  
  βοΈ Response: String "μ’μμ μΆκ° μλ£ or μ’μμ μ·¨μ μλ£" 
  
               // λ‘κ·ΈμΈνμ§ μμ μ¬μ©μμ κ²½μ° 400μλ¬μ λ©μμ§("μ’μμλ₯Ό νκΈ° μν΄μλ λ‘κ·ΈμΈμ΄ νμν©λλ€.")
               
## 7. νμκ°μ
  βοΈ Api: /user/signup
  
  βοΈ Request: Form data = 
  
                        {String "userEmail":"userEmail",
  
                          String "password":"password",
  
                          String "nickname":"nickname"}
  
  βοΈ Response: Success -> λ‘κ·ΈμΈ(/user/login)μΌλ‘ redirect
  
              // λ€μμ κ²½μ°μ 400μλ¬μ λ©μμ§ : μ€λ³΅ μ΄λ©μΌ μ‘΄μ¬, μ€λ³΅ λλ€μ μ‘΄μ¬, ν¨μ€μλμ λλ€μ ν¬ν¨, λλ€μμ΄ 3κΈμ λ―Έλ§, λλ€μμ νΉμλ¬Έμλ νκΈ ν¬ν¨
              
## 8. λ‘κ·ΈμΈ
  βοΈ Api: /user/login
  
  βοΈ Request: Form data = 
  
                        {String "username":"userEmail(μ€μ λ‘λ μ΄λ©μΌκ°μΈλ°, nameλΆλΆλ§ usernameμ΄μμ..^^ μ£μ‘ν©λλ€!!)",
  
                          String "password":"password"}
  
  βοΈ Response: Success
  
              // μ΄λ©μΌ λλ λΉλ°λ²νΈ λΆμΌμΉμ μ¬νμΈ μκ΅¬νλ 400
  
  
