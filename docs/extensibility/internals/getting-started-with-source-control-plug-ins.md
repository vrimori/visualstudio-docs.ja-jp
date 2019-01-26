---
title: ソース管理プラグインの概要 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d3d756984f27c66a74e1342aeac99c4fd076ff8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55028435"
---
# <a name="get-started-with-source-control-plug-ins"></a>ソース管理プラグインを概要します。
ソース管理プラグインを作成するには、ソース コントロールのプラグイン API で定義された関数を実装する DLL を作成する必要があり、次の DLL の登録を[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース コードのバージョン管理に使用できるようにします。  
  
 ソース管理プラグイン API (バージョン 1.1、1.2、および 1.3) の 3 つのバージョンでは、ソース管理プラグインを使用できます。ここに記載されているソース コントロールのプラグイン API はバージョン 1.3 です。 これは、デザインは、ソース管理プラグインと完全に互換性がバージョン 1.1 および 1.2 をサポートします。 [新機能についてはソース管理プラグイン API バージョン 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)セクションで、ソース管理プラグイン API の最新バージョンでサポートされる新機能について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: ソース管理プラグインのインストールします。](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 ソース管理 DLL を接続するために必要なレジストリ エントリを作成する方法について説明します。  
  
 [ソース管理プラグイン API バージョン 1.3 の新機能新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 バージョン 1.3 でソース管理プラグイン API に加えられた変更の概要を簡単に説明します。  
  
 [新機能については、ソース管理プラグイン API バージョン 1.2 です。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 バージョン 1.2 でソース管理プラグイン API に加えられた変更の概要を簡単に説明します。  
  
## <a name="related-sections"></a>関連項目  
 [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)  
 ソース管理プラグイン API のすべての要素の完全な一覧を提供します。  
  
 [ソース管理プラグインを作成します。](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 ソース管理プラグインの SDK を定義し、含まれているリソースについて説明します。