---
title: "機能拡張インターフェイスによる UI 機能のカスタマイズ"
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
  - "ICustomTaskPaneConsumer インターフェイス"
  - "IRibbonExtensibility インターフェイス"
  - "UI のカスタマイズ [Visual Studio での Office 開発]"
  - "ユーザー インターフェイス [Visual Studio での Office 開発]、カスタマイズ"
  - "アプリケーション レベルのアドイン [Visual Studio での Office 開発]、機能拡張インターフェイス"
  - "カスタマイズ (UI 機能を) [Visual Studio での Office 開発]"
  - "FormRegionStartup インターフェイス"
  - "アドイン [Visual Studio での Office 開発]、機能拡張インターフェイス"
  - "機能拡張インターフェイス [Visual Studio での Office 開発]"
ms.assetid: 3f3f7908-9404-4eda-8899-4d18c75e3b4a
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 機能拡張インターフェイスによる UI 機能のカスタマイズ
  Visual Studio に含まれる Office 開発ツールは、VSTO アドインにおけるカスタム作業ウィンドウ、リボンのカスタマイズ、および Outlook フォーム領域の作成に使用可能な、多数の実装の詳細を処理するクラスとデザイナーを提供します。 ただし、特別な要件がある場合、各機能の*拡張インターフェイス*を自分で実装することもできます。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## 機能拡張インターフェイスの概要  
 Microsoft Office は、COM VSTO アドインがリボンなどの特定の機能をカスタマイズするために実装可能な、機能拡張インターフェイスのセットを定義します。 これらのインターフェイスは、アクセスを提供する機能に対するフル コントロールを提供します。 ただし、これらのインターフェイスを実装するには、マネージ コードにおける COM 相互運用性について一定の知識が必要です。 これらのインターフェイスのプログラミング モデルは、.NET Framework に慣れた開発者にとって直観的でない場合もあります。  
  
 Visual Studio に含まれる Office プロジェクト テンプレートを使用して VSTO アドインを作成する場合、リボンなどの機能をカスタマイズするために機能拡張インターフェイスを実装する必要はありません。[!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] はこれらのインターフェイスを実装します。 代わりに、Visual Studio が提供する、より直観的なクラスおよびデザイナーを使用することもできます。 ただし、必要に応じて、機能拡張インターフェイスを直接 VSTO アドインに実装することもできます。  
  
 これらの機能に関して Visual Studio が提供するクラスとデザイナーの詳細については、「[カスタム作業ウィンドウ](../vsto/custom-task-panes.md)」、「[リボン デザイナー](../vsto/ribbon-designer.md)」、および「[Outlook フォーム領域の作成](../vsto/creating-outlook-form-regions.md)」を参照してください。  
  
## VSTO アドインに実装できる機能拡張インターフェイス  
 次の表に、実装可能な機能拡張インターフェイスとそれらをサポートするアプリケーションを示します。  
  
|Interface|説明|アプリケーション|  
|---------------|--------|--------------|  
|<xref:Microsoft.Office.Core.IRibbonExtensibility>|このインターフェイスを実装してリボン UI をカスタマイズします。 **Note:**  プロジェクトに **\[リボン \(XML\)\]** 項目を追加して、VSTO アドインに既定の <xref:Microsoft.Office.Core.IRibbonExtensibility> 実装を生成できます。 詳細については、「[リボン XML](../vsto/ribbon-xml.md)」を参照してください。|Excel<br /><br /> [!INCLUDE[InfoPath_15_short](../vsto/includes/infopath-15-short-md.md)]<br /><br /> InfoPath 2010<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> プロジェクト<br /><br /> Visio<br /><br /> Word|  
|<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>|このインターフェイスを実装してカスタム作業ウィンドウを作成します。|Excel<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Word|  
|<xref:Microsoft.Office.Interop.Outlook.FormRegionStartup>|このインターフェイスを実装して Outlook フォーム領域を作成します。|Outlook|  
  
 Microsoft Office で定義されている機能拡張インターフェイスには他に、<xref:Microsoft.Office.Core.IBlogExtensibility>、<xref:Microsoft.Office.Core.EncryptionProvider>、および <xref:Microsoft.Office.Core.SignatureProvider> があります。 Visual Studio では、Office プロジェクト テンプレートを使用して VSTO アドインにこれらのインターフェイスを実装することはサポートされていません。  
  
## 機能拡張インターフェイスの使用法  
 機能拡張インターフェイスを使用して UI をカスタマイズするには、VSTO アドイン プロジェクトに適切なインターフェイスを実装します。 次に、そのインターフェイスを実装するクラスのインスタンスを返すために、<xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> メソッドをオーバーライドします。  
  
 Outlook 用 VSTO アドインにおける <xref:Microsoft.Office.Core.IRibbonExtensibility>、<xref:Microsoft.Office.Core.ICustomTaskPaneConsumer>、および <xref:Microsoft.Office.Interop.Outlook.FormRegionStartup> インターフェイスの実装方法を示すサンプル アプリケーションについては、「[Office 開発のサンプル](../vsto/office-development-samples.md)」の UI マネージャーのサンプルを参照してください。  
  
### 機能拡張インターフェイスの実装例  
 次のコード例は、カスタム作業ウィンドウを作成するための <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> インターフェイスの簡単な実装を示します。 この例では、2 つのクラスを定義しています。  
  
-   `TaskPaneHelper` クラスは、カスタム作業ウィンドウの作成と表示を行うための <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> を実装します。  
  
-   `TaskPaneUI` クラスは、作業ウィンドウの UI を提供します。`TaskPaneUI` クラスの属性により、クラスが COM に対して可視化され、Microsoft Office アプリケーションがクラスを発見することができるようになります。 この例で、UI は空の <xref:System.Windows.Forms.UserControl> ですが、コードを修正してコントロールを追加できます。  
  
    > [!NOTE]  
    >  `TaskPaneUI` クラスを COM に公開するには、プロジェクトの **\[COM の相互運用機能の登録\]** プロパティを設定する必要もあります。  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_SimpleExtensibilityInterface#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#1)]  
  
 <xref:Microsoft.Office.Core.ICustomTaskPaneConsumer> の実装の詳細については、Microsoft Office ドキュメントの「[Creating Custom Task Panes in the 2007 Office System \(2007 Office システムにおけるカスタム作業ウィンドウの作成\)](http://msdn.microsoft.com/ja-jp/256313db-18cc-496c-a961-381ed9ca94be)」を参照してください。  
  
### RequestService メソッドのオーバーライド例  
 次のコード例は、前のコード例から <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> クラスのインスタンスを返すために `TaskPaneHelper` メソッドをオーバーライドする方法を示します。*serviceGuid* パラメーターの値を検査し、要求されているインターフェイスを特定して、そのインターフェイスを実装するオブジェクトを返します。  
  
 [!code-csharp[Trin_SimpleExtensibilityInterface#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_SimpleExtensibilityInterface#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_SimpleExtensibilityInterface/VB/ThisAddIn.vb#2)]  
  
## 参照  
 [Office 開発のサンプルとチュートリアル](../vsto/office-development-samples-and-walkthroughs.md)   
 [VSTO アドインのプログラミング](../vsto/programming-vsto-add-ins.md)   
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [その他の Office ソリューションから VSTO アドインのコードを呼び出す](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)   
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)  
  
  