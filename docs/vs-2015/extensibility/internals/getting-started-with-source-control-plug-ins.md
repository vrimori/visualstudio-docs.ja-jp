---
title: ソース管理プラグインの概要 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e521c239f474d803da5b615de8dcf1cf56d37df3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755242"
---
# <a name="getting-started-with-source-control-plug-ins"></a>ソース管理プラグイン入門
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース管理プラグインを作成するには、ソース コントロールのプラグイン API で定義された関数を実装する DLL を作成する必要があり、次の DLL の登録を[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ソース コードのバージョン管理に使用できるようにします。  
  
 ソース管理プラグイン API (バージョン 1.1、1.2、および 1.3) の 3 つのバージョンでは、ソース管理プラグインを使用できます。ここに記載されているソース コントロールのプラグイン API はバージョン 1.3 です。 これは、デザインは、ソース管理プラグインと完全に互換性がバージョン 1.1 および 1.2 をサポートします。 [ソース管理プラグイン API バージョン 1.3 で新](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)セクションで、ソース管理プラグイン API の最新バージョンでサポートされる新機能について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: ソース管理プラグインのインストール](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 ソース管理 DLL を接続するために必要なレジストリ エントリを作成する方法について説明します。  
  
 [ソース管理プラグイン API バージョン 1.3 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 バージョン 1.3 でソース管理プラグイン API に加えられた変更の概要を簡単に説明します。  
  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 バージョン 1.2 でソース管理プラグイン API に加えられた変更の概要を簡単に説明します。  
  
## <a name="related-sections"></a>関連項目  
 [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)  
 ソース管理プラグイン API のすべての要素の完全な一覧を提供します。  
  
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 ソース管理プラグインの SDK を定義し、含まれているリソースについて説明します。

