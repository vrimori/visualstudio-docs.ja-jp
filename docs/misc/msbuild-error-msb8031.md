---
title: "MSBuild エラー MSB8031 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSB8031"
ms.assetid: ebfaca51-fd91-4b04-8194-b4fdededd5fe
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB8031
MSB8031  
  
 MFC プロジェクトで MBCS エンコーディングを使用するには、追加のライブラリをダウンロードし、インストールする必要があります。  
  
 MFC DLL の MBCS バージョンは Visual Studio に含まれていませんが、これらのバージョンは MFC MBCS DLL アドオンで利用できます。このアドオンは Visual Studio ユーザーであればダウンロードできます。  このアドオンをインストールしていない状態で、MBCS 文字セットを使用する MFC プロジェクトをビルドしようとすると、リンカーは DLL を検索できず、ビルドは失敗します。  
  
### このエラーを解決するには  
  
1.  MSDN ダウンロード センターから [MBCS MFC DLL アドオンをダウンロード](http://go.microsoft.com/fwlink/?LinkId=299009)するか、可能である場合はプロジェクトを UNICODE 文字セットに変換します。  
  
## 参照  
 [MFC MBCS DLL アドオン](/visual-cpp/mfc/mfc-mbcs-dll-add-on)