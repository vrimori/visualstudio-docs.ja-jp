---
title: ソース管理ストアをプロジェクト フォルダーの比較 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2e0f6f2185385ee7ec3942556a43f58d43e7a4da
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>ソース管理ストアをローカルのプロジェクト フォルダーの省略可能な比較
ソース制御関数を使用して、ローカルのプロジェクト フォルダーとソース コントロール間の比較が行われますプラグイン API 1.2 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)と[SccDirDiff](../../extensibility/sccdirdiff-function.md)です。  
  
 内で**ソリューション エクスプ ローラー**、個々 のファイルではなく、フォルダーが選択されている場合、**バージョンを比較**ショートカット メニューを新しい起動[SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)と[SccDirDiff](../../extensibility/sccdirdiff-function.md)ソース管理プラグインでします。  
  
## <a name="new-capability-flags"></a>新しい機能フラグ  
 `SCC_CAP_DIRECTORYDIFF`  
  
 `SCC_CAP_DIRECTORYCHECKOUT`  
  
## <a name="new-functions"></a>新しい関数  
 [SccDirDiff](../../extensibility/sccdirdiff-function.md)  
  
 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)  
  
 `SccDirQueryInfo`前に関数を呼び出して`SccDirDiff`作業ディレクトリがソース管理されているかを判断します。 `SccDirDiff`関数は、現在のローカル ディレクトリと、対応するソース コントロール フォルダーとの違いを表示します。 このコマンドでは、ソース管理プラグイン ディレクトリに変更の一覧を表示するように求めます。 ソース管理プラグインは、相違点を表示する独自の UI を提供します。  
  
> [!NOTE]
>  この関数と同じコマンド フラグを使用して[SccDiff](../../extensibility/sccdiff-function.md)です。 ソース管理プラグイン プロバイダーとしてディレクトリを"クイック diff"操作をサポートしないようにしてもかまいません。  
  
## <a name="see-also"></a>関連項目  
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)