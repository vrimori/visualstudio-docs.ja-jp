---
title: "この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrAppModel_SingleInstanceCantConnect"
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした
この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした。 この問題の考えられる原因の一部は次のとおりです。  
  
-   元のインスタンスが応答を停止した。  
  
-   カーネル オブジェクトを作成するためのアクセス許可がアプリケーションにない。 カーネル オブジェクトの詳細については、「[Mutexes](../Topic/Mutexes.md)」を参照してください。  
  
     カーネル オブジェクトの基本名は、アセンブリの GUID、メジャー バージョン番号、およびマイナー バージョン番号を連結したものです。 たとえば、基本名が `3639f15d-9547-43da-8145-60da347829915.1` になる可能性があります。  
  
### アプリケーションを開発しているときに、このエラーを解決するには  
  
1.  アプリケーションが応答していない状態にならないことを確認します。  
  
2.  カーネル オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。  
  
3.  アプリケーションの元のインスタンスを再起動します。  
  
4.  コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。  
  
5.  エラーが発生した状況を記録して、Microsoft 製品サポート サービスに電話でご連絡ください。  
  
## 参照  
 [NIB: 方法: アプリケーションのインスタンス化動作を指定する \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/48539ad8-d960-4210-beab-ee65f6c6dc6e)   
 [デバッガーの基本事項](../debugger/debugger-basics.md)   
 [PAVEOVER 製品のサポートとアクセシビリティ](http://msdn.microsoft.com/ja-jp/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)