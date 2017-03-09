---
title: "MSBuild エラー MSB3126 | Microsoft Docs"
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
  - "GenerateManifest.FileAssociationsNotInstalled"
helpviewer_keywords: 
  - "MSB3126"
ms.assetid: 0c92cbb6-9100-4433-8113-f2f3a1432243
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild エラー MSB3126
**MSB3126: アプリケーションはファイルの関連付けを使用していますが、インストール用としてマークされていません。  ファイルの関連付けは、Web ブラウザーでホストされているアプリケーションなど、インストールされていないアプリケーションには使用できません。**  
  
 このエラーは、アプリケーションがファイルの関連付けを使用するように構成されているのに、アプリケーションのインストール モードがオンライン専用に設定されている場合に発生します。  通常、オンライン専用のアプリケーションはブラウザーで実行するため、ファイルの関連付けは使用できません。  
  
### このエラーを解決するには  
  
-   **\[インストール モードと設定\]** を **\[アプリケーションはオフラインでも利用できる \(スタート メニューから起動可能\)\]** に設定します。  詳細については、「[方法: ClickOnce のオフラインまたはオンラインのインストール モードを指定する](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)」を参照してください。  
  
## 参照  
 [\[発行\] ページ \(プロジェクト デザイナー\)](../Topic/Publish%20Page,%20Project%20Designer.md)   
 [ClickOnce アプリケーション マニフェスト](../deployment/clickonce-application-manifest.md)