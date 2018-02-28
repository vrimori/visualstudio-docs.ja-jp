---
title: "Windows ランタイムの非同期メソッドの使用 | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JavaScript, Windows Runtime asynchronous methods
ms.assetid: 70756833-44f7-4383-827f-2ac781558082
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 215a04a2f3f875743a7fbf910a3a565cf34fb558
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="using-windows-runtime-asynchronous-methods"></a>Windows ランタイムの非同期メソッドの使用
完了するまでに時間のかかるメソッドをはじめ、Windows ランタイム メソッドの多くは、非同期メソッドです。 一般に、非同期メソッドは非同期アクションまたは非同期操作を返します (`Windows.Foundation.IAsyncAction`、`Windows.Foundation.IAsyncOperation`、`Windows.Foundation.IAsyncActionWithProgress`、`Windows.Foundation.IAsyncOperationWithProgress` など)。 JavaScript では、これらのメソッドは [CommonJS/Promises/A](http://go.microsoft.com/fwlink/p/?LinkId=244434) のパターンで表されます。 つまり、これらのメソッドは [then](https://msdn.microsoft.com/en-us/library/windows/apps/br229728.aspx) 関数を含む Promise オブジェクトを返すため、操作が成功した場合に結果を処理する `completed` 関数を提供する必要があります。 エラー ハンドラーを提供しない場合は、`then` 関数の代わりに [done](https://msdn.microsoft.com/en-us/library/windows/apps/hh701079.aspx) 関数を使用してください。  
  
> [!IMPORTANT]
>  Windows ランタイムの機能は Internet Explorer で実行されるアプリでは使用できません。  
  
## <a name="examples-of-asynchronous-methods"></a>非同期メソッドの例  
 この例の `then` 関数は、`createResourceAsync` メソッドの完了後の値を表すパラメーターを取ります。  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
        console.log("New item is: " + newItem.id);  
            });  
```  
  
 この例では、`createResourceAsync` メソッドが失敗した場合、エラー状態の約束オブジェクトが返されますが、例外はスローされません。 以下のように `then` 関数を使用すると、エラーを処理することができます。  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
    .then(function(newItem) {   
              console.log("New item is: " + newItem.id);  
          }  
          function(err) {  
              console.log("Got error: " + err.message);  
          });  
```  
  
 エラーを明示的に処理しない一方、メソッドに例外をスローさせる場合には、代わりに `done` 関数を使用できます。  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .done(function(newItem) {   
               console.log("New item is: " + newItem.id);  
            });  
```  
  
 3 つ目の関数を使用して、操作完了に向けた進行状況を表示することもできます。  
  
```JavaScript  
client.createResourceAsync(uri, description, item)  
    // Success.  
      .then(function(newItem) {   
               console.log("New item is: " + newItem.id);  
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
  
 非同期プログラミングの詳細については、「[JavaScript での非同期プログラミング (HTML)](https://msdn.microsoft.com/en-us/library/windows/apps/hh700330.aspx)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [JavaScript での Windows ランタイムの使用](../jswinrt/using-the-windows-runtime-in-javascript.md)