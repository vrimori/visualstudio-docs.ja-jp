---
title: "永続化され、実行されているテーブルを文書化 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7f48a1acdad3856e7334ce6a86b48e67c880f9c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-and-the-running-document-table"></a>永続化と実行中のドキュメント テーブル
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE、プロジェクトは、完全にサービスを使用しているためには、プロジェクト項目を取得するには、持続性の管理を担当<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>です。 ドキュメントは、永続化では、Visual Studio 環境の基本単位です。 プロジェクトでは、開いたり、保存、および実行中のドキュメント テーブル (RDT) すべての開いているドキュメントの状態を追跡するリソースを持つドキュメントの名前の変更を調整します。  
  
## <a name="managing-persistence"></a>持続性の管理  
 プロジェクト管理環境の永続性サービスの実装することによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>インターフェイスです。 環境には、ドキュメント自体を永続化を直接要求する、ときに、所有しているプロジェクト (または階層) ドキュメントを保存するように求めます。 これにより、そのプロジェクト項目のデータをローカル ファイル、リモート ファイル、データベースを repository、またはその他のメディアに保存するプロジェクトです。  
  
 グローバル環境は、RDT を保持します。 環境は、すべての開いているウィンドウのエントリを維持しにできるように、RDT 内のドキュメントは、ソリューションが閉じられるタイミングなどの特別な通知を受信します。 さらに、RDT できるようになりますで、対応するノードを追跡するために、環境の**ソリューション エクスプ ローラー**です。 RDT は、プロジェクト ファイルとプロジェクト項目ドキュメントの両方を含む、開く、永続化できるオブジェクトごとの 1 つのレコードを保持します。  
  
## <a name="see-also"></a>参照  
 [実行中のドキュメント テーブル](../../extensibility/internals/running-document-table.md)   
 [IDE での選択と通貨](../../extensibility/internals/selection-and-currency-in-the-ide.md)