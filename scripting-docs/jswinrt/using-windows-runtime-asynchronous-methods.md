---
title: "Windows ランタイム非同期メソッドの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows ランタイム非同期メソッド"
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Windows ランタイム非同期メソッドの使用
完了するまでに時間のかかるメソッドをはじめ、Windows ランタイム メソッドの多くは、非同期メソッドです。  一般に、非同期メソッドは非同期アクションまたは非同期操作を返します \(`Windows.Foundation.IAsyncAction`、`Windows.Foundation.IAsyncOperation`、`Windows.Foundation.IAsyncActionWithProgress`、`Windows.Foundation.IAsyncOperationWithProgress` など\)。  JavaScript では、非同期メソッドは [CommonJS\/Promises\/A](http://go.microsoft.com/fwlink/p/?LinkId=244434) のパターンで表現されます。  つまり、非同期メソッドは [then](http://msdn.microsoft.com/ja-jp/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 関数を格納した約束オブジェクトを返すため、操作が成功した場合に結果を処理する `completed` 関数を提供する必要があります。  エラー ハンドラーを提供しない場合は、[then](http://msdn.microsoft.com/ja-jp/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 関数の代わりに [done](http://msdn.microsoft.com/ja-jp/9a5e6877-a2cf-421f-a91e-37d84ccb40da) を使用してください。  
  
> [!IMPORTANT]
>  Windows ランタイムの機能は Internet Explorer で実行されるアプリでは使用できません。  
  
## 非同期メソッドの例  
 この例の [then](http://msdn.microsoft.com/ja-jp/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 関数は、`createResourceAsync` メソッドの完了後の値を表すパラメーターを取ります。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 この例では、`createResourceAsync` メソッドが失敗した場合、エラー状態の約束オブジェクトが返されますが、例外はスローされません。  以下のように [then](http://msdn.microsoft.com/ja-jp/c63904fc-465b-4fd5-a1d6-e4fb200248e7) 関数を使用すると、エラーを処理することができます。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 エラーを明示的に処理しない一方、メソッドに例外をスローさせる場合には、代わりに [done](http://msdn.microsoft.com/ja-jp/9a5e6877-a2cf-421f-a91e-37d84ccb40da) 関数を使用できます。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 3 つ目の関数を使用して、操作完了に向けた進行状況を表示することもできます。  
  
```javascript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            },  
    // Error.  
            function(error) {   
               alert("Failed to create a resource.");  
            },  
    // Progress.  
            function(progress, resultSoFar) {   
               setProgressBar(progress);  
            });  
```  
  
 非同期プログラミングについて詳しくは、「[Asynchronous programming](http://msdn.microsoft.com/ja-jp/904ff97c-bb36-4ac5-9eda-a961e3639415)」を参照してください。  
  
## 参照  
 [JavaScript での Windows ランタイムの使用](../jswinrt/using-the-windows-runtime-in-javascript.md)