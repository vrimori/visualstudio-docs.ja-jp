---
title: 削除する ~ SAK ファイル |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 61227652bf191280f69466f127c4a400ea43856e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129642"
---
# <a name="elimination-of-sak-files"></a>削除する ~ SAK ファイル
ソース管理プラグイン API 1.2 では、~ SAK ファイルが置き換えられて機能フラグと、ソース管理プラグインは、MSSCCPRJ ファイルと共有チェック アウトをサポートするかどうかを検出する新しい関数。  
  
## <a name="sak-files"></a>~ SAK ファイル  
 Visual Studio .NET 2003 が付きます。 一時ファイルを作成した ~ SAK です。 これらのファイルは、ソース管理プラグインをサポートしているかどうかに使用されます。  
  
-   MSSCCPRJ です。SCC ファイルです。  
  
-   複数 (共有) のチェック アウトします。  
  
 プラグイン ソース管理プラグイン API 1.2 で提供される高度な機能をサポートする、IDE は、新機能、フラグ、および、次のセクションで詳しく関数を使用して一時ファイルを作成するこれらの機能を検出できます。  
  
## <a name="new-capability-flags"></a>新しい機能フラグ  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>新しい関数  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 ソース管理プラグインは、(共有) の複数のチェック アウトをサポートしているかどうかは、宣言、`SCC_CAP_MULTICHECKOUT`機能と実装、`SccIsMultiCheckOutEnabled`関数。 この関数は、ソース管理対象のプロジェクトのいずれかをチェック アウト操作が発生するたびに呼び出されます。  
  
 場合は、ソース管理プラグインは、作成して、MSSCCPRJ の使用をサポートします。SCC ファイル、その宣言、`SCC_CAP_SCCFILE`機能と実装、 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)です。 この関数は、ファイルの一覧と呼びます。 この関数を返します`TRUE/FALSE`Visual Studio が、MSSCCPRJ を使用するかどうかを示すためにファイルごとにします。そのファイルを SCC です。 ソース管理プラグインは、これらの新機能と機能をサポートしないように選択した場合、は、次のレジストリ キーを使用して、これらのファイルの作成を無効にすることができます。  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]"DoNotCreateTemporaryFilesInSourceControl"= dword:00000001  
  
> [!NOTE]
>  このレジストリ キーが dword:00000000 に設定されている場合は、存在しない、されているキーと等価である Visual Studio はまだ一時ファイルを作成しようとします。 ただし、レジストリ キーが dword:00000001 に設定されている場合 Visual Studio はしよう一時ファイルを作成します。 代わりに、ソース管理プラグインが、MSSCCPRJ をサポートしていないことを想定します。SCC ファイル共有チェック アウトをサポートしていません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)