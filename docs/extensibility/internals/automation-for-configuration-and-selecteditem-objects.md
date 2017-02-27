---
title: "構成および SelectedItem オブジェクトのための自動化 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "オートメーション [Visual Studio SDK] SelectedItem オブジェクト"
  - "オートメーション [Visual Studio SDK] の構築します。"
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# 構成および SelectedItem オブジェクトのための自動化
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のビルド選択した項目の処理を自動化できます。  
  
## ビルドのオートメーション  
 ビルド構成には <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> を実行するときに提供されるオートメーション モデルがあります。  詳細については、「[ビルド構成について](../../ide/understanding-build-configurations.md)」を参照してください。  
  
 VSPackage を作成し構成オプションを設定するにはオートメーション モデルを使用する必要があります。  
  
## SelectedItem のオートメーション  
 Visual Studio が標準の実装が含まれているため `SelectedItem` のオブジェクトの実装を提供する必要はありません。  ただし`SelectedItem`オブジェクトを実装できます。  `SelectedItem` のインターフェイスを実装するオブジェクトを含むなりVSITEMID に設定 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> のメソッドに <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> の呼び出しに応答を返します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [オートメーション モデルに貢献しています。](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [ビルド構成について](../../ide/understanding-build-configurations.md)