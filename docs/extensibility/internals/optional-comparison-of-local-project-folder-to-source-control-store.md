---
title: "ソース管理ストアをプロジェクト フォルダーの比較 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: b2ed6955e5ba6fa334cc89a0c2ea8a3d4248f362
ms.lasthandoff: 02/22/2017

---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>ソース管理ストアをローカルのプロジェクト フォルダーのオプションの比較
ソースの制御関数を使用してローカルのプロジェクト フォルダー、ソース管理との比較を行うプラグイン API 1.2 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)と[SccDirDiff](../../extensibility/sccdirdiff-function.md)します。  
  
 内で**ソリューション エクスプ ローラー**個々 のファイルではなく、フォルダーが選択されている場合は、**バージョンを比較**ショートカット メニューを呼び出す新しい[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)と[SccDirDiff](../../extensibility/sccdirdiff-function.md)ソース管理プラグインでします。  
  
## <a name="new-capability-flags"></a>新しい機能フラグ  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>新しい関数  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo`関数は、前に呼び出されます`SccDirDiff`作業ディレクトリがソース管理されているかを判断します。 `SccDirDiff`関数は、現在のローカル ディレクトリと対応するソース管理フォルダーの相違点を表示します。 このコマンドでは、ソース管理プラグイン ディレクトリに変更の一覧を表示するように依頼します。 ソース管理プラグインでは、相違点を表示する UI を提供します。  
  
> [!NOTE]
>  この関数と同じコマンドのフラグを使用して[SccDiff](../../extensibility/sccdiff-function.md)します。 ソース管理プラグイン プロバイダーとして、ディレクトリの「クイック比較」操作をサポートしていないこともできます。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能します。](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
