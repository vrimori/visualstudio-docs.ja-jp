---
title: ドキュメント テーブルの持続性と実行 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb66051d3a1ab0119f4b80a68f0f2990e569fe8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929771"
---
# <a name="persistence-and-the-running-document-table"></a>ドキュメント テーブルの保存と実行
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE、プロジェクトは、完全にサービスを使用して、行うには、そのプロジェクト項目の永続化を管理する責任を負います<xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>します。 ドキュメントは、Visual Studio 環境での永続化の基本単位です。 プロジェクトでは、開いている、保存、および実行されているドキュメント テーブル (RDT) すべての開いているドキュメントの状態を追跡するリソースとドキュメントの名前に変更を調整します。  
  
## <a name="managing-persistence"></a>持続性の管理  
 プロジェクト管理環境の永続性サービスの実装することによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>インターフェイス。 環境では、ドキュメント自体を永続化を直接確認、中にドキュメントを保存する所有元のプロジェクト (または階層) を確認します。 これにより、ローカル ファイル、リモート ファイル、データベース、リポジトリ、またはその他のメディアにそのプロジェクト項目のデータを保存するプロジェクト。  
  
 グローバル環境、RDT を保持します。 環境は、すべての開いているウィンドウのエントリを維持しにできるようにすると、RDT のドキュメントは、ソリューションを閉じたときなど、特別な通知を受信します。 さらに、RDT により、環境の対応するノードを追跡するために**ソリューション エクスプ ローラー**します。 RDT のでは、プロジェクト ファイルとプロジェクト項目のドキュメントの両方を含む、オープンな永続化できるオブジェクトごとに 1 つのレコードを保持します。  
  
## <a name="see-also"></a>関連項目  
 [実行中の Document テーブル](../../extensibility/internals/running-document-table.md)   
 [IDE での選択と通貨](../../extensibility/internals/selection-and-currency-in-the-ide.md)