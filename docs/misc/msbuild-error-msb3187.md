---
title: "MSBuild エラー MSB3187 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateManifest.PlatformMismatch"
helpviewer_keywords: 
  - "MSB3187"
ms.assetid: c5e93c14-b099-4176-bf1b-dbecc47fb3fd
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3187
**MSB3187: 参照アセンブリ '\<アセンブリ\>' は、アプリケーションとは異なるプロセッサをターゲットにしています。**  
  
 この警告は、アプリケーションのターゲット プラットフォーム \(プロセッサ アーキテクチャ\) がニュートラル \(MSIL\) で、参照アセンブリがニュートラルでない場合、またはアプリケーションのアーキテクチャがニュートラルではなく、依存関係がニュートラルの場合に生成されます。  どちらもプラットフォーム ニュートラルではない場合も、アーキテクチャが一致している必要があります。  また、アプリケーション アーキテクチャとエントリ ポイント アセンブリ アーキテクチャは常に一致する必要があります。  
  
### このエラーを解決するには  
  
-   アプリケーションのターゲット プラットフォーム \(プロセッサ アーキテクチャ\) がすべての参照アセンブリとエントリ ポイント アセンブリ アーキテクチャに一致することを確認します。  
  
## 参照  
 [\[ビルドの詳細設定\] ダイアログ ボックス \(Visual Basic\)](../Topic/Advanced%20Compiler%20Settings%20Dialog%20Box%20\(Visual%20Basic\).md)   
 [\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)