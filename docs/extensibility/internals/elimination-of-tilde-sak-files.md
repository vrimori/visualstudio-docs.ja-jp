---
title: 排除 ~ SAK ファイル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- temporary files
- ~sak files
- source control plug-ins, ~SAK files
ms.assetid: 5277b5fa-073b-4bd1-8ba1-9dc913aa3c50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701bb929bae7b5103e274810cf0ad3a222118781
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54951275"
---
# <a name="elimination-of-sak-files"></a>排除 ~ SAK ファイル
ソース管理プラグイン API 1.2 では、 *~ SAK*ファイル機能フラグによって置き換えられ、ソースかどうかを検出する新しい関数は、プラグインのサポートを制御、 *MSSCCPRJ*ファイルと共有チェック アウトします。  
  
## <a name="sak-files"></a>~ SAK ファイル  
Visual Studio .NET 2003 の付いた一時ファイルを作成する *~ SAK*します。 これらのファイルは、ソース管理プラグインをサポートしているかどうかに使用されます。  
  
- *MSSCCPRJ.SCC*ファイル。  
  
- 複数の (共有) チェック アウトします。  
    
プラグインのソース管理プラグイン API 1.2 で提供される高度な機能をサポートする、IDE は、新機能、フラグ、および、次のセクションに記載された関数を使用して一時ファイルを作成することがなくこれらの機能を検出できます。  
  
## <a name="new-capability-flags"></a>新しい機能フラグ  
 `SCC_CAP_SCCFILE`  
  
 `SCC_CAP_MULTICHECKOUT`  
  
## <a name="new-functions"></a>新しい関数  
 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)  
  
 [SccIsMultiCheckoutEnabled](../../extensibility/sccismulticheckoutenabled-function.md)  
  
 ソース管理プラグインは、(共有) の複数のチェック アウトをサポートしているかどうかは、宣言、`SCC_CAP_MULTICHECKOUT`機能と実装、`SccIsMultiCheckOutEnabled`関数。 この関数は、ソース管理対象のプロジェクトのいずれかのチェック アウト操作が発生するたびに呼び出されます。  
  
 作成と使用のソース管理プラグインがサポートしている場合、 *MSSCCPRJ.SCC*を宣言し、ファイル、`SCC_CAP_SCCFILE`機能と実装、 [SccWillCreateSccFile](../../extensibility/sccwillcreatesccfile-function.md)します。 この関数は、ファイルの一覧が呼び出されます。 関数を返します`TRUE' or 'FALSE`Visual Studio を使用する必要がありますかを指定する各ファイルに対して、 *MSSCCPRJ.SCC*ファイル。 ソース管理プラグインは、これらの新機能と機能をサポートしないように選択した場合、は、次のレジストリ キーを使用して、これらのファイルの作成を無効にすることができます。  
  
 **[HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl]DoNotCreateTemporaryFilesInSourceControl** = *dword:00000001*  
  
> [!NOTE]
>  このレジストリ キーが設定されている場合*dword:00000000*、存在しない場合は、キーに相当および一時ファイルを作成する Visual Studio が再度試みられます。 ただし、レジストリ キー設定されている場合*dword:00000001*、Visual Studio が一時ファイルを作成しません。 ソース管理プラグインがサポートされていないことを前提に代わりに、 *MSSCCPRJ.SCC*ファイルし、は共有チェック アウトをサポートしていません。  
  
## <a name="see-also"></a>関連項目  
 [新機能については、ソース管理プラグイン API バージョン 1.2 です。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)