---
title: どのような&#39;ソース新プラグイン API バージョン 1.3 の制御 |Microsoft Docs
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
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 58756bde7f3eb9fbc0f42bf494d82e8cc508796e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793921"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>どのような&#39;ソース新プラグイン API バージョン 1.3 を制御します。
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

ソース管理プラグイン API バージョン 1.3 より高度な制御を提供する次の関数について説明します。  
  
## <a name="changes"></a>変更  
 次の関数は、新しいソース管理プラグイン API バージョン 1.3 には。  
  
|関数|概要|  
|--------------|--------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|により、報告する追加機能ビット|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|ローカル ディスク上のよりもバージョン管理データベースに新しいバージョンがファイルを調べることができます。|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|指定したファイルの 名前の変更 (名前変更、追加、および削除) の状態を調べることができます。|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|ディレクトリおよびファイルのバージョン管理データベースでの調べることができます。|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|バージョン管理データベースからファイルの指定された一覧を現在のプロジェクトに追加します。|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|サイレント"Get"(ユーザー インターフェイスは表示されません)、指定されたファイルの実行します。|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|ユーザー固有のオプションにアクセスをできます。|  
  
## <a name="see-also"></a>関連項目  
 [はじめに](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [ソース管理プラグイン API バージョン 1.2 の新機能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)

