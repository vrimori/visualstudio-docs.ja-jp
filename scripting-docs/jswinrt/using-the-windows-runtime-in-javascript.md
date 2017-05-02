---
title: "JavaScript での Windows ランタイムの使用 | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, Windows ランタイム"
ms.assetid: 90658546-f746-4e34-a7d1-71cf9ee322a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JavaScript での Windows ランタイムの使用
JavaScript を使用して [!INCLUDE[win8_appname_long](../javascript/includes/win8-appname-long-md.md)] または Windows Phone ストア アプリを作成する場合、ネイティブ JavaScript オブジェクト、メソッド、プロパティを使用するのとほとんど同じように、Windows ランタイム クラス、メソッド、プロパティを使用できます。  このトピックでは、JavaScript の概要を説明し、JavaScript で Windows ランタイム API を使用する際の基本概念を説明するトピックへのリンクを記載します。リンク先のトピックでは、Windows ランタイム型の表現方法、非同期 Windows ランタイム メソッドを使用する方法、Windows ランタイム イベントをリッスンして処理する方法などを説明しています。  
  
 JavaScript のリファレンス ドキュメントについては、「[JavaScript 言語リファレンス](../javascript/javascript-language-reference.md)」を参照してください。  
  
> [!IMPORTANT]
>  Windows ランタイムの機能は Internet Explorer で実行されるアプリでは使用できません。  
  
## Windows ランタイムのリファレンス ドキュメント  
 リファレンス ドキュメントについては、「[Windows Runtime reference](http://msdn.microsoft.com/ja-jp/8fe97dbf-8cd4-435f-b481-9e83d0519f9e)」を参照してください。  コード例は、JavaScript だけでなく、C\+\+、C\#、および Visual Basic でも利用できます。  
  
## C\+\+、C\#、または Visual Basic での Windows ランタイム コンポーネントの作成  
 JavaScript で使用できる Windows ランタイム コンポーネントを作成する方法とガイドラインについては、「[Windows ランタイム コンポーネントの作成](http://msdn.microsoft.com/library/9a6b8f0a-7d5e-40a0-a9c5-a59b4908e133)」を参照してください。  
  
## Windows ランタイム機能の表記規則  
 JavaScript での Windows ランタイム機能の表記規則は、他の言語での表記規則とは少し異なります。  
  
-   名前空間とクラスは、Pascal 形式で表記されます。  
  
    ```javascript  
    Windows.Deployment.PackageInfo;  
    ```  
  
-   クラスのメンバー \(メソッドとプロパティを含む\) と構造および列挙体のメンバーは、Camel 形式で表記されます。  
  
    ```javascript  
    Deployment.PackageInfo.createPackage();  
    ```  
  
-   イベント名は、小文字で表記されます。  
  
    ```javascript  
    dataTransferManager.ontargetapplicationchosen;  
    ```  
  
## 参照  
 [Windows ランタイム API を使用する場合の考慮事項](../jswinrt/considerations-when-using-the-windows-runtime-api.md)   
 [Windows ランタイム非同期メソッドの使用](../jswinrt/using-windows-runtime-asynchronous-methods.md)   
 [JavaScript での Windows ランタイム イベントの処理](../jswinrt/handling-windows-runtime-events-in-javascript.md)   
 [Windows ランタイム型の JavaScript 表現](../jswinrt/javascript-representation-of-windows-runtime-types.md)   
 [Windows ランタイムの DateTime および TimeSpan の JavaScript 投影](../jswinrt/windows-runtime-datetime-and-timespan-representations.md)