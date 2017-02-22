---
title: "/SafeMode (devenv.exe) | Microsoft Docs"
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
  - "/SafeMode Devenv スイッチ"
  - "Devenv, /SafeMode スイッチ"
  - "SafeMode スイッチ"
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] をセーフ モードで起動し、既定の環境とサービスだけを読み込みます。  
  
## 構文  
  
```  
devenv /SafeMode   
```  
  
## 解説  
 このスイッチは、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] が起動したときに、すべてのサード パーティ VSPackage を読み込まないようにし、これによりプログラムの実行を安定したものにします。  
  
## Description  
 セーフ モードで [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動する例を次に示します。  
  
## コード  
  
```  
Devenv.exe /SafeMode  
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)