---
title: "非共有メンバーを参照するには、オブジェクト参照が必要です | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30469"
  - "vbc30469"
helpviewer_keywords: 
  - "BC30469"
ms.assetid: af503e8b-2e1f-4f91-a07f-b1ddd73dd4a6
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 非共有メンバーを参照するには、オブジェクト参照が必要です
コード内で非共有メンバーを参照しましたが、オブジェクト参照を指定していませんでした。 共有されていないメンバーを修飾するためにクラス名自体は使用できません。 インスタンスは最初にオブジェクト変数として宣言してから、変数名によって参照しなければなりません。  
  
 **エラー ID:** BC30469  
  
### このエラーを解決するには  
  
1.  インスタンスをオブジェクト変数として宣言します。  
  
2.  変数名によってインスタンスを参照します。  
  
## 参照  
 [ビルド内にありません: クラスについて](http://msdn.microsoft.com/ja-jp/cc2355a2-cb98-4353-9440-736585aec46c)   
 [ビルド内にありません: Visual Basic の共有メンバー](http://msdn.microsoft.com/ja-jp/dbc3783f-83a2-4225-995d-c2d6d025663d)   
 [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)   
 [ビルド内にありません: 同じ名前を持つ複数の変数がある場合に参照を解決する](http://msdn.microsoft.com/ja-jp/9601e39f-1911-44e1-ace5-3f6e090408b9)