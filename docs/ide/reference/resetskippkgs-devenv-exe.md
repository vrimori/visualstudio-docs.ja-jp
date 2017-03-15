---
title: "/ResetSkipPkgs (devenv.exe) | Microsoft Docs"
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
  - "/ResetSkipPkgs DEVENV スイッチ"
  - "Devenv, /ResetSkipPkgs スイッチ"
  - "ResetSkipPkgs スイッチ"
ms.assetid: 7ece64f9-cfa4-4b34-b0d9-1c338b9557b3
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /ResetSkipPkgs (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

問題のある VSPackage の読み込みを避けるためにユーザーによって VSPackage に追加された、読み込みを省略するためのオプションをすべて解除します。その後、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動させます。  
  
## 構文  
  
```  
Devenv /ResetSkipPkgs  
```  
  
## 解説  
 SkipLoading タグがあると VSPackage の読み込みが無効になり、VSPackage の読み込みを再有効化するタグが解除されます。  
  
## 使用例  
 すべての SkipLoading タグを解除する例を次に示します。  
  
```  
Devenv.exe /ResetSkipPkgs  
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)