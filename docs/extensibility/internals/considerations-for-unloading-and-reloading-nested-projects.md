---
title: "入れ子になったプロジェクトのアンロードと再ロードに関する考慮事項 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "入れ子になったプロジェクトをアンロードして再読み込みします。"
  - "プロジェクト [Visual Studio SDK] アンロード中で入れ子になったの再読み込み"
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# 入れ子になったプロジェクトのアンロードと再ロードに関する考慮事項
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

入れ子になったプロジェクトを実行するとプロジェクトのアンロードと再読み込みすると追加の手順を実行する必要があります。  正しくソリューションのイベントのリスナーに通知するために正しく `OnBeforeUnloadProject` と `OnAfterLoadProject` のイベントを発生させる必要があります。  
  
 このようにこれらのイベントを発生させる必要があるのは1 から SCC `Get` 操作が \(SCC\) ソース・コード管理にサーバーから項目を削除し新しいものとして追加しないことです。  この場合新しいファイルが異なる場合 SCC から読み込まれすべてのファイルのアンロードと再読み込みする必要があります。  SCC は `ReloadItem` を呼び出します。  その呼び出しの実装ではプロジェクトを削除し`OnBeforeUnloadProject` と `OnAfterLoadProject` を呼び出すに `IVsFireSolutionEvents` を実行してから再作成することです。  この実装を行うとSCC はプロジェクトを一時的に削除され再度追加されたことを通知を受け取ります。  したがってSCC はプロジェクトがサーバーから実際に削除され再度追加されているプロジェクトについては動作しません。  
  
## プロジェクトを再読み込みする  
 入れ子になったプロジェクトの再読み込みをサポートするには<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> のメソッドを実装します。  `ReloadItem` の実装では入れ子になったプロジェクトを閉じてから再作成します。  
  
 通常プロジェクトが再読み込みされる場合に<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> と `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)` のイベントを発生させます。  ただし削除され再読み込みされたプロジェクトの場合親プロジェクトはIDE ではなくプロセスを開始します。  親プロジェクトをソリューション内のイベントは発生せずIDE のプロセスの初期化に関する情報がないためイベントは発生しません。  
  
 このプロセスは<xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> インターフェイスの親プロジェクトでは `QueryInterface`<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> のインターフェイスから処理します。  `IVsFireSolutionEvents` 入れ子に したプロジェクトをアンロードするにはIDE を `OnBeforeUnloadProject` のイベントを発生させる指示すると同じプロジェクトを再読み込みするに `OnAfterLoadProject` の関数がイベントを発生させます。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [入れ子のプロジェクト](../../extensibility/internals/nesting-projects.md)