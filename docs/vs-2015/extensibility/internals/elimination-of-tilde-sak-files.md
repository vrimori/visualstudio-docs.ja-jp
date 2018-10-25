---
title: 排除 ~ SAK ファイル |Microsoft Docs
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
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7422b0dae02b12d731713f6da416361798d3276
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824311"
---
# <a name="elimination-of-sak-files"></a>~SAK ファイルの削除
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース管理プラグイン API 1.2 では、~ SAK ファイルは、機能フラグと、ソース管理プラグインが MSSCCPRJ ファイルと共有チェック アウトをサポートしているかどうかを検出する新しい関数で置き換えられています。  
  
## <a name="sak-files"></a>~ SAK ファイル  
 Visual Studio .NET 2003 の付いた一時ファイルを作成する ~ SAK します。 これらのファイルは、ソース管理プラグインをサポートしているかどうかに使用されます。  
  
- MSSCCPRJ します。SCC ファイルです。  
  
- 複数の (共有) チェック アウトします。  
  
  プラグインのソース管理プラグイン API 1.2 で提供される高度な機能をサポートする、IDE は、新機能、フラグ、および、次のセクションに記載された関数を使用して一時ファイルを作成することがなくこれらの機能を検出できます。  
  
## <a name="new-capability-flags"></a>新しい機能フラグ  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>新しい関数  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 ソース管理プラグインは、(共有) の複数のチェック アウトをサポートしているかどうかは、宣言、`SCC_CAP_MULTICHECKOUT`機能と実装、`SccIsMultiCheckOutEnabled`関数。 この関数は、ソース管理対象のプロジェクトのいずれかのチェック アウト操作が発生するたびに呼び出されます。  
  
 ソース管理プラグインの場合は、作成して、MSSCCPRJ の使用をサポートしています。SCC ファイル、その宣言、`SCC_CAP_SCCFILE`機能と実装、 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)します。 この関数は、ファイルの一覧が呼び出されます。 関数を返します`TRUE/FALSE`の各ファイルを Visual Studio で、MSSCCPRJ を使用する必要があるかどうかを示すためにします。そのファイルを SCC です。 ソース管理プラグインは、これらの新機能と機能をサポートしないように選択した場合、は、次のレジストリ キーを使用して、これらのファイルの作成を無効にすることができます。  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateTemporaryFilesInSourceControl"= dword:00000001  
  
> [!NOTE]
>  このレジストリ キーが dword:00000000 に設定されている場合は、される存在しない場合は、キーと等価ですが、Visual Studio はまだ一時ファイルを作成しようとします。 ただし、レジストリ キーが dword:00000001 に設定されている場合 Visual Studio が一時ファイルを作成する試行はありません。 代わりに、MSSCCPRJ をソース管理プラグインがサポートしていないことが前提としています。SCC ファイル共有チェック アウトをサポートしていません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

