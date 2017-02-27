---
title: "方法 : ビジュアライザーをインストールする | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "デバッガー, ビジュアライザー"
  - "ビジュアライザー, インストール"
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# 方法 : ビジュアライザーをインストールする
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

作成したビジュアライザーは、インストールして初めて [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] で使用できるようになります。  ビジュアライザーのインストールは簡単です。  
  
> [!NOTE]
>  **ストア** アプリでは、標準的なテキスト、HTML、XML、および JSON ビジュアライザーがサポートされています。  カスタム \(ユーザーが作成した\) ビジュアライザーはサポートされていません。  
  
### ビジュアライザーをインストールするには  
  
1.  作成したビジュアライザーを含むダイナミック リンク ライブラリ \(DLL: Dynamic Link Library\) を探します。  
  
2.  DLL を次のいずれかの場所にコピーします。  
  
    -   *VisualStudioInstallPath*`\Common7\Packages\Debugger\Visualizers`  
  
    -   `My Documents\`*VisualStudioVersion*`\Visualizers`  
  
3.  マネージ ビジュアライザーをリモート デバッグで使用するには、DLL をリモート コンピューター上の同じパスにコピーします。  
  
4.  デバッグ セッションを再開します。  
  
## 参照  
 [ビジュアライザー](../debugger/create-custom-visualizers-of-data.md)   
 [方法 : ビジュアライザーを記述する](../debugger/how-to-write-a-visualizer.md)