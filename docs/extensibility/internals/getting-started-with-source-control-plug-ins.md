---
title: "ソース管理プラグインの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理プラグインを作業の開始"
  - "取得 started、ソース管理プラグイン"
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# ソース管理プラグインの概要
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソース管理プラグインを作成するには次の DLL をソース管理プラグイン API で定義した関数を作成して実行する次にソース・コードのバージョン コントロールで使用できるようにするために [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DLL を登録できます。  
  
 ソース管理プラグイン API の 3 種類のバージョン \(Version 1.11.2および 1.3\) はソース管理のプラグインで使用できます。  ここに記載されているソース管理プラグイン API ではバージョン 1.3 になります。  バージョン 1.1 と 1.2 をサポートするソース管理プラグインに完全に対応するデザインされています。  [ソース管理プラグイン API バージョン 1.3 の新機能します。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) のセクションではソース管理プラグイン API の最新バージョンでサポートされている新しい機能について詳しく説明します。  
  
## このセクションの内容  
 [方法: ソース管理プラグインのインストール](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 ソース管理プラグイン DLL を組み込むために必要なレジストリ エントリを作成する方法について説明します。  
  
 [ソース管理プラグイン API バージョン 1.3 の新機能します。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 バージョン 1.3 のソース管理プラグイン API に加えられた変更の概要について説明します。  
  
 [ソース管理プラグイン API バージョン 1.2 の新機能します。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 バージョン 1.2 のソース管理プラグイン API に加えられた変更の概要について説明します。  
  
## 関連項目  
 [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)  
 ソース管理プラグイン API のすべての要素の一覧を示します。  
  
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 ソース管理プラグイン SDK を定義し追加したリソースについて説明します。