---
title: "[設定のインポートとエクスポート] コマンド | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Tools.ImportandExportSettings"
helpviewer_keywords: 
  - "Tools.ImportandExportSettings"
  - "[設定のインポートとエクスポート] コマンド"
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# [設定のインポートとエクスポート] コマンド
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 設定をインポート、エクスポート、またはリセットします。  
  
## 構文  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## スイッチ  
 \/export:`filename`  
 省略可能です。  現在の設定を指定されたファイルにエクスポートします。  
  
 \/import:`filename`  
 省略可能です。  設定を指定されたファイルにインポートします。  
  
 \/reset  
 省略可能です。  現在の設定をリセットします。  
  
## 解説  
 このコマンドをスイッチ指定なしで実行すると、**設定のインポートとエクスポート**ウィザードが開きます。  詳細については、「[How to: Share Settings Between Computers or Visual Studio Versions](http://msdn.microsoft.com/ja-jp/1131fb10-35c1-42da-9cd8-91aa3235b882)」を参照してください。  
  
## 使用例  
 次のコマンドを実行すると、現在の設定が `MyFile.vssettings` ファイルにエクスポートされます。  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## 参照  
 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio コマンド](../../ide/reference/visual-studio-commands.md)