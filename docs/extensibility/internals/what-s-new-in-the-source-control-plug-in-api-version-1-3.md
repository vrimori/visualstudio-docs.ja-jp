---
title: "どのような &#39; のソース コントロール プラグイン API バージョン 1.3 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bd0c23258034fb99f5e2e4e0c86ca9e61c3d68ab
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>どのような &#39; ソース管理プラグイン API のバージョン 1.3 の
ソース管理プラグイン API バージョン 1.3 より高度な制御を提供する次の関数について説明します。  
  
## <a name="changes"></a>変更  
 次の関数は、ソース管理プラグイン API バージョン 1.3 新しいです。  
  
|関数|概要|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|により、報告する追加機能ビット|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|ローカル ディスクにより、バージョン管理データベースに新しいバージョンがファイルを調べることができます。|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|で指定したファイルは、名前の変更 (名前変更、追加、および削除) の状態を調べる|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|ディレクトリおよびファイルのバージョン管理データベースで調べることができます。|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|現在のプロジェクトをバージョン管理データベースから指定されたファイルの一覧を追加します。|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|サイレント"Get"(ユーザー インターフェイスは表示されません)、指定されたファイルの実行します。|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|ユーザー固有のオプションにアクセスをできます。|  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)