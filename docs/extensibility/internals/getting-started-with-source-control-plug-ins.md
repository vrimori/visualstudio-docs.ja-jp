---
title: ソース管理プラグインの概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f5c88d932fd2915273c86924d2df8f1233baeed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128918"
---
# <a name="getting-started-with-source-control-plug-ins"></a>ソース管理プラグインの概要
ソース管理プラグインを作成するには、ソース管理プラグイン API で定義された関数を実装する DLL を作成する必要がありますで DLL を登録し[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ソース コードのバージョン管理に使用できるようにします。  
  
 ソース管理プラグイン API (バージョン 1.1、1.2、および 1.3) の 3 つのバージョンのソース管理プラグインを利用できます。ここに記載されてソース コントロールのプラグイン API とは、バージョン 1.3 です。 ソース管理プラグインを完全に互換性がある設計されたバージョン 1.1 および 1.2 をサポートします。 [ソース管理プラグイン API バージョン 1.3 の新](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)セクションで、ソース管理プラグイン API の最新のバージョンでサポートされる新機能について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: ソース管理プラグインのインストール](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 ソース管理 DLL を接続するために必要なレジストリ エントリを作成する方法について説明します。  
  
 [ソース管理プラグイン API バージョン 1.3 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 ソース コントロールのプラグイン API のバージョン 1.3 に加えられた変更の概要を簡単に説明します。  
  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 ソース コントロールのプラグイン API のバージョン 1.2 に加えられた変更の概要を簡単に説明します。  
  
## <a name="related-sections"></a>関連項目  
 [ソース管理プラグイン](../../extensibility/source-control-plug-ins.md)  
 ソース管理プラグイン API 内のすべての要素の完全な一覧を提供します。  
  
 [ソース管理プラグインの作成](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 ソース管理プラグイン SDK を定義して、含まれているリソースを記述します。