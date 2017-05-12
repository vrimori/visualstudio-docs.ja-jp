---
title: "&#39;this&#39; に割り当てることはできません。 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5000"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# &#39;this&#39; に割り当てることはできません。
**this** に値を代入しようとしました。  **this**  は、次のいずれかを参照する [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] キーワードです:  
  
-   現在メソッドを実行しているオブジェクト  
  
-   現在のメソッドがない場合 \(またはメソッドが他のどのオブジェクトにも属していない場合\) はグローバル オブジェクト  
  
 メソッドは、オブジェクトによって呼び出された [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 関数です。  メソッド内部では、**this** キーワードは、メソッドの呼び出し元のオブジェクトへの参照で、**new** 演算子を使用して呼び出したクラス コンストラクターによって作成されたオブジェクトに対する参照でもあります。  
  
 メソッド内部では、**this** を使用して現在のオブジェクトを参照できますが、**this** に新しい値を代入することはできません。  
  
### このエラーを解決するには  
  
-   **this** に値を代入しないでください。  インスタンス化されたオブジェクトのプロパティまたはメソッドにアクセスするには、ドット演算子を使用します \(circle**.**radius など\)。  
  
    > [!NOTE]
    >  ユーザーが作成した変数に [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の予約語である **this** という名前を付けることはできません。  
  
## 参照  
 [this ステートメント](../../javascript/reference/this-statement-javascript.md)   
 [JScript スクリプトのトラブルシューティング](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)