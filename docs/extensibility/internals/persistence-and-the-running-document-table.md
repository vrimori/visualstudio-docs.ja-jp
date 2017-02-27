---
title: "永続化と実行中の Document テーブル | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "永続化ストアを管理します。"
  - "IVsPersistHierarchyItem インターフェイスを実装します。"
  - "アーキテクチャでは、永続化"
  - "実行中の document テーブル (RDT) アーキテクチャ"
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 永続化と実行中の Document テーブル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE、プロジェクトは、完全にサービスを使用しているためには、自分のプロジェクト項目の永続性の管理を担当 <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>します。 ドキュメントは、Visual Studio 環境での永続化の基本単位です。 プロジェクトでは、開く、保存、および実行されている document テーブル \(RDT\) はすべての開いているドキュメントの状態を追跡するリソースを持つドキュメントの名前の変更を調整します。  
  
## 持続性の管理  
 プロジェクト管理環境の永続性サービスの実装することによって、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> インターフェイスです。 環境には、ドキュメント自体を永続化を直接要求する、中にドキュメントを保存する所有元のプロジェクト \(または階層\) を確認します。 これにより、ローカル ファイル、リモート ファイル、データベース、リポジトリ、またはその他のメディアに、プロジェクト項目のデータを保存するプロジェクト。  
  
 グローバル環境では、RDT を保持します。 環境は、すべての開いているウィンドウのエントリを維持し、やすいことが RDT 内のドキュメントが、ソリューションを閉じたときなど、特殊な通知を受信します。 さらに、RDT これにより、環境の対応するノードを追跡するために **ソリューション エクスプ ローラー**します。 RDT では、プロジェクト ファイルとプロジェクト項目ドキュメントの両方を含む、オープンで永続化できるオブジェクトごとの 1 つのレコードを保持します。  
  
## 参照  
 [実行中のドキュメント テーブル](../../extensibility/internals/running-document-table.md)   
 [選択と、IDE 内の通貨](../../extensibility/internals/selection-and-currency-in-the-ide.md)