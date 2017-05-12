---
title: "Office プロジェクト内のオブジェクトへのグローバル アクセス"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "Globals クラス、オブジェクトのグローバル アクセス"
  - "ワークシート [Visual Studio での Office 開発]、グローバル アクセス"
  - "ドキュメント [Visual Studio での Office 開発]、グローバル アクセス"
  - "イベント ハンドラー [Visual Studio での Office 開発]"
  - "ThisWorkbook_Startup"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]"
  - "アドイン [Visual Studio での Office 開発]、イベント"
  - "ブック [Visual Studio での Office 開発]、グローバル アクセス"
  - "ThisWorkbook_Shutdown"
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発]"
  - "Startup イベント"
  - "Shutdown イベント"
  - "プロジェクト [Visual Studio での Office 開発]、グローバル アクセス"
  - "Office ドキュメント [Visual Studio での Office 開発]、グローバル アクセス"
  - "ThisAddin_Startup"
  - "イベント [Visual Studio での Office 開発]"
  - "ThisAddIn_Shutdown"
ms.assetid: f6a7f0ef-75d0-4a9b-9aec-be95ffa26adf
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Office プロジェクト内のオブジェクトへのグローバル アクセス
  Office プロジェクトを作成すると、Visual Studio は自動的に `Globals` という名前のクラスをプロジェクトに生成します。`Globals` クラスを使用して、プロジェクト内の任意のコードから実行時に異なる複数のプロジェクト項目にアクセスすることができます。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Globals クラスを使用する方法  
 `Globals` はプロジェクト内の特定の項目への参照を保持する静的クラスです。`Globals` クラスを使用することで、実行時にプロジェクト内の任意のコードから次の項目へとアクセスすることができます。  
  
-   Excel ブックまたはテンプレート プロジェクトの `ThisWorkbook` および `Sheet`*n* クラス。 これらのオブジェクトは、`Globals.ThisWorkbook` および `Sheet`*n* プロパティを使用してアクセスすることができます。  
  
-   Word 文書またはテンプレート プロジェクトの `ThisDocument` クラス。 このオブジェクトには、`Globals.ThisDocument` プロパティを使用してアクセスすることができます。  
  
-   VSTO アドイン プロジェクトの `ThisAddIn` クラス。 このオブジェクトには、`Globals.ThisAddIn` プロパティを使用してアクセスすることができます。  
  
-   リボン デザイナーを使用してカスタマイズした、プロジェクト内のすべてのリボン。 リボンには、`Globals.Ribbons` プロパティを使用してアクセスすることができます。 詳細については、「[実行時のリボンへのアクセス](../vsto/accessing-the-ribbon-at-run-time.md)」を参照してください。  
  
-   Outlook VSTO アドイン プロジェクトのすべての Outlook フォーム領域。 フォーム領域には、`Globals.FormRegions` プロパティを使用してアクセスすることができます。 詳細については、「[実行時におけるフォーム領域へのアクセス](../vsto/accessing-a-form-region-at-run-time.md)」を参照してください。  
  
-   [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] または [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] をターゲットとするプロジェクトで実行時にリボン コントロールおよびホスト項目を作成できるようにするファクトリ オブジェクト。 このオブジェクトには、`Globals.Factory` プロパティを使用してアクセスすることができます。 このオブジェクトは、次のいずれかのインターフェイスを実装するクラスのインスタンスです。  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 たとえば、`Globals.Sheet1` プロパティを使用すると、Excel のドキュメントレベルのプロジェクトの操作ウィンドウでユーザーがボタンをクリックした場合に `Sheet1` の <xref:Microsoft.Office.Tools.Excel.NamedRange> コントロールにテキストを挿入することができます。  
  
 [!code-csharp[Trin_VstcoreProgramming#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstcoreProgramming#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#1)]  
  
## Globals クラスの初期化  
 ドキュメントまたは VSTO アドインが完全に初期化する前に `Globals` クラスの使用を試みるコードは、実行時の例外をスローする場合があります。 たとえば、クラス レベルの変数の宣言が `Globals` を使用することで失敗する場合があります。これは、宣言されたオブジェクトがインスタンス化される前に、`Globals` クラスがすべてのホスト項目への参照を使用して初期化されない可能性があるためです。  
  
> [!NOTE]  
>  `Globals` クラスは設計時に初期化されることはありませんが、コントロールのインスタンスがデザイナーによって作成されます。 これは、ユーザー コントロール クラス内から `Globals` クラスのプロパティを使用するユーザー コントロールを作成する場合、そのプロパティが返されたオブジェクトを使用しようとする前に **null** を返すかどうかを決定する必要があることを意味します。  
  
## 参照  
 [実行時のリボンへのアクセス](../vsto/accessing-the-ribbon-at-run-time.md)   
 [実行時におけるフォーム領域へのアクセス](../vsto/accessing-a-form-region-at-run-time.md)   
 [ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)   
 [Document ホスト項目](../vsto/document-host-item.md)   
 [Workbook ホスト項目](../vsto/workbook-host-item.md)   
 [Worksheet ホスト項目](../vsto/worksheet-host-item.md)   
 [Office ソリューションのコードの記述](../vsto/writing-code-in-office-solutions.md)  
  
  