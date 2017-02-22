---
title: "プロジェクトの種類を展開します。 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "プロジェクト [Visual Studio SDK] マネージ コード"
  - "プロジェクト [Visual Studio SDK] アグリゲーター"
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# プロジェクトの種類を展開します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 新しいプロジェクトの種類アグリゲーター \(ProjectAggregator2.dll\) とも再頒布 \(ProjectAggregator2.msi\) 用の Windows インストーラー パッケージをインストールします。 マネージ コード プロジェクトの種類に対して新しいアグリゲーターを使用する必要があります。 ProjectAggregator2 で策の制限の動作、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトのマネージ コード プロジェクトの種類が正常に動作するを防ぐアグリゲーター。 次の手順では、新しいアグリゲーターを使用する、VSPackage を変更する方法について説明します。  
  
1.  NativeHierarchyWrapper プロジェクトをソリューションから削除します。  
  
2.  セットアップからすべての NativeHierarchyWrapper バイナリを削除します。  
  
3.  セットアップに ProjectAggregator2.msi を追加します。