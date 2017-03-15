---
title: "提供されるサービス (ソース コントロールの vs パッケージ) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "サービスのソース管理パッケージ"
  - "サービスのソース管理パッケージ"
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# 提供されるサービス (ソース コントロールの vs パッケージ)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

サービスは機能によって VSPackage 内と Visual Studio 統合開発環境とともにインストールされる VSPackage で共有される \(IDE\) 主要な機構です。  Visual Studio IDE のサービスも重要度の詳細については[使用して、サービスを提供します。](../../extensibility/using-and-providing-services.md) を参照してください。  
  
## ソース管理サービス  
 Visual Studio によってそのレベル サービスとパッケージ レベル サービスの 2 のレイヤーを提供します。  Visual Studio IDE はIDE でネイティブ レベルのサービスを提供します。  パッケージ ソース管理ではこれらのサービスの一部を実装します。  VSPackage としてソース管理パッケージは独自のプライベート ソース管理サービスを提供することによりソース管理機能を共有します。  ソース管理パッケージはVisual Studio IDE で使用できるコントラクトの形式で実行されるソース コントロールの関連のインターフェイスのセットをカプセル化します。  
  
## 参照  
 [デザイン要素](../../extensibility/internals/source-control-vspackage-design-elements.md)