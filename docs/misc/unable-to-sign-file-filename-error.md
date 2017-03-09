---
title: "ファイル &#39;&lt;filename&gt;&#39; に署名できません: &lt;error&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31028"
  - "vbc31028"
helpviewer_keywords: 
  - "BC31028"
ms.assetid: 2cb22e75-5ee2-4e07-afc0-680a0bd543d4
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ファイル &#39;&lt;filename&gt;&#39; に署名できません: &lt;error&gt;
指定したファイルに署名しようとするときに、エラーが発生しました。 このエラーには、いくつかの原因の可能性があります。  
  
-   アクセス許可が不十分です。  
  
-   Authenticode 署名に必要なシステム ファイルが不足しています。  
  
-   存在しない証明書または秘密キー ファイルへの参照があります。  
  
-   ファイル名または URL のスペルが間違っています。  
  
 **エラー ID:** BC31028  
  
### このエラーを解決するには  
  
1.  正しい証明書と秘密キーのファイル名を入力します。  
  
2.  Authenticode 署名を使用している場合は、ファイル Signcode.exe および Javasign.dll が存在することと、その読み取り専用属性が設定されていないことを確認します。  
  
3.  ファイルへの `Write` アクセス許可があることを確認します。  
  
## 参照  
 [File Signing Tool \(Signcode.exe\)](http://msdn.microsoft.com/ja-jp/2d299154-34ea-41ba-ad12-17075bb7e1db)   
 [Deployment and Authenticode Signing](http://msdn.microsoft.com/ja-jp/ecc3f059-da2e-445b-9b87-5b2978e2f8b2)