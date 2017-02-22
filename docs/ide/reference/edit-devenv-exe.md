---
title: "/Edit (devenv.exe) | Microsoft Docs"
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
  - "/Edit Devenv スイッチ"
  - "Devenv, /edit スイッチ"
ms.assetid: 02b3d6e7-a2b1-4d83-a747-aa8c2fb758b7
caps.latest.revision: 6
caps.handback.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Edit (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定されたファイルを [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスで開きます。  
  
## 構文  
  
```  
Devenv /edit [file1[ file2]]  
```  
  
## 引数  
 `file1`  
 省略可能です。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスで開くファイルです。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のインスタンスが存在しない場合は、簡略化されたウィンドウ レイアウトで新しいインスタンスが作成され、この新しいインスタンスで `file1` が開かれます。  
  
 `file2`  
 省略可能です。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスで開く 1 つ以上の追加ファイルです。  
  
## 解説  
 ファイルが指定されず、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスが存在する場合は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスがフォーカスを受け取ります。  ファイルが指定されず、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスも存在しない場合は、簡略化されたウィンドウ レイアウトで [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の新しいインスタンスが作成されます。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスがモーダル状態である \(たとえば、[&#91;オプション&#93; ダイアログ ボックス](../../ide/reference/options-dialog-box-visual-studio.md)が開いている\) 場合は、モーダル状態が終了したときに、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスでファイルが開かれます。  
  
## 使用例  
 次の例では、`MyFile.cs` ファイルを [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既存のインスタンスで開きます。既存のインスタンスが存在しない場合は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の新しいインスタンスでファイルを開きます。  
  
```  
devenv /edit MyFile.cs  
```  
  
## 参照  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)