---
title: "その他のファイル プロジェクト | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ファイル、既存のファイルをソリューションに追加します。"
  - "他のファイル プロジェクト"
  - "ソリューション項目フォルダー"
  - "その他のファイル プロジェクトを開いているファイル"
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# その他のファイル プロジェクト
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ユーザーがでプロジェクト項目を開くとそのファイルに IDE の割り当てはソリューションのすべてのプロジェクトのメンバーではない項目があります。  
  
 再生がどのエディターを使用するかを決定する最も重要な役割をユーザーがでプロジェクト項目を開くとき。  プロジェクトはプロジェクト固有のエディターまたは標準エディターを使用すると特定のファイルを開くように設計できます。  
  
 プロジェクト固有のエディターは通常ユーザーに特別な知識がある場合またはプロジェクトの特別なインターフェイスを使用する必要があります。  詳細については、「[方法: プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)」を参照してください。  
  
 標準エディターはプロジェクトの特定の拡張子のファイルを開くことができます。  ユーザーはいくつかの標準 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]エディターのテキスト エディターなどの場合はプロジェクトをカスタマイズしてパブリックの文字を保持できます。  標準エディターは <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> のメソッドを使用して作成されます。  
  
 プロジェクト項目を開くことができるソリューションのプロジェクトが応答しない IDE で開いているファイルにそのほかのファイル プロジェクトと呼ばれる特別なプロジェクトを提供します。  
  
 この特殊なプロジェクトはプロジェクトのコンテキストの外部にあるファイルの先頭を指定します。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> のメソッドの処理中にそのファイルはきわめて低い優先順位で常プロジェクトに応答します。  したがってそのファイルは開いているファイルできる任意の優先順位のプロジェクトに生成を常に記述されます。  
  
 そのほかのファイル プロジェクトはユーザーが明示的に ENT0ENT \[出力\] ダイアログ ボックスで作成する必要はありません。  またそのほかのファイル プロジェクトではプロジェクト メンバーのリストを管理しません。  これは各ユーザーの最近使用したファイルの一覧を記録するにはオプション機能を使用します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [方法: プロジェクトに固有のエディターを開く](../../extensibility/how-to-open-project-specific-editors.md)   
 [方法: 標準のエディターを開く](../../extensibility/how-to-open-standard-editors.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [プロジェクトとプロジェクト項目テンプレートを追加します。](../../extensibility/internals/adding-project-and-project-item-templates.md)