---
title: "/ResetSettings (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "/ResetSettings DEVENV スイッチ"
  - "Devenv, /ResetSettings スイッチ"
  - "ResetSettings スイッチ"
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既定の設定を復元し、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE を自動的に開始します。  指定の .vssettings ファイルに準じた設定にリセットすることもできます。  
  
 既定の設定は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の初回起動時に選択したプロファイルによって決定されます。  
  
## 構文  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## 引数  
 `SettingsFile`  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に適用する .vssettings ファイルの完全パスとファイル名です。  
  
 全般的な開発設定のプロファイルを復元するには、`General` を使用します。  
  
## 解説  
 `SettingsFile` が指定されていない場合、次回 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動したときに、既定の設定のコレクションを選択するよう要求されます。  
  
## 使用例  
 `MySettings.vssettings` ファイルに保存された設定を適用するコマンド ラインを次に示します。  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## 参照  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)