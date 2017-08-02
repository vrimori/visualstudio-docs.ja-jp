---
title: "方法 : Visual Basic プロジェクトのコードを VBA に公開する"
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
  - "ドキュメント レベルのカスタマイズ [Visual Studio での Office 開発], 公開 (コードを)"
  - "公開 (コードを VBA に)"
  - "ホスト項目 [Visual Studio での Office 開発], 公開 (コードを VBA に)"
  - "VBA [Visual Studio での Office 開発], 公開 (ドキュメント レベルのカスタマイズ内のコードを)"
  - "Visual Basic [Visual Studio での Office 開発], 公開 (コードを VBA に)"
ms.assetid: dc74f3ea-3f78-47f8-8a82-a67896144dd9
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# 方法 : Visual Basic プロジェクトのコードを VBA に公開する
  2 種類のコードを連携させる場合は、[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] プロジェクトのコードを Visual Basic for Applications \(VBA\) コードに公開することができます。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Visual Basic プロセスは Visual C\# プロセスとは異なります。  詳細については、「[方法 : Visual C&#35; プロジェクトのコードを VBA に公開する](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)」を参照してください。  
  
 ホスト項目クラスにあるコードに対するプロセスと、その他のクラスにあるコードに対するプロセスは異なります。  
  
-   [ホスト項目クラスにあるコードを公開する](#HostItemCode)  
  
-   [ホスト項目クラスにはないコードを公開する](#NonHostItem)  
  
 ![ビデオへのリンク](~/docs/data-tools/media/playvideo.gif "ビデオへのリンク") 関連のビデオ デモについては、「[How Do I: Call VSTO Code from VBA? \(操作方法: VBA から VSTO コードを呼び出す\)](http://go.microsoft.com/fwlink/?LinkId=136757)」を参照してください。  
  
##  <a name="HostItemCode"></a> ホスト項目クラスにあるコードを公開する  
 ホスト項目クラスにある Visual Basic コードを VBA コードで呼び出すことができるようにするには、ホスト項目の **EnableVbaCallers** プロパティを **True** に設定します。  
  
 ホスト項目クラスのメソッドを公開し、VBA から呼び出す方法を説明するチュートリアルについては、「[チュートリアル : VBA から Visual Basic プロジェクトのコードを呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)」を参照してください。  ホスト項目の詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
#### ホスト項目クラスにあるコードを VBA に公開するには  
  
1.  マクロをサポートする Word 文書、Excel ブック、または Excel テンプレートに基づく、VBA コードが既に含まれているドキュメント レベルの [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] プロジェクトを開くか、または作成します。  
  
     マクロをサポートするドキュメント ファイル形式の詳細については、「[VBA とドキュメント レベルのカスタマイズの結合](../vsto/combining-vba-and-document-level-customizations.md)」を参照してください。  
  
    > [!NOTE]  
    >  この機能は、Word テンプレート プロジェクトでは使用できません。  
  
2.  ドキュメント内の VBA コードがユーザーにマクロの有効化を要求することなく実行可能であることを確認します。  Word または Excel のセキュリティ センターの設定にある信頼できる場所の一覧に Office プロジェクトの場所を追加することで、VBA コードを信頼して実行できるようになります。  
  
3.  VBA に公開するプロパティ、メソッド、またはイベントを、プロジェクト内のいずれかのホスト項目クラスに追加し、新しいメンバーを **Public** として宣言します。  クラスの名前は、アプリケーションによって異なります。  
  
    -   Word プロジェクトの場合、ホスト項目クラスの名前は既定で `ThisDocument` になります。  
  
    -   Excel プロジェクトの場合、ホスト項目クラスの名前は既定で `ThisWorkbook`、`Sheet1`、`Sheet2`、および `Sheet3` になります。  
  
4.  ホスト項目の **EnableVbaCallers** プロパティを **True** に設定します。  このプロパティは、ホスト項目をデザイナーで開いたときに **\[プロパティ\]** ウィンドウで利用できます。  
  
     このプロパティを設定すると、Visual Studio によって自動的に **ReferenceAssemblyFromVbaProject** プロパティが **True** に設定されます。  
  
    > [!NOTE]  
    >  ブックまたは文書に VBA コードが含まれていない場合、またはドキュメント内の VBA コードに実行に対する信頼が付与されていない場合に、**EnableVbaCallers** プロパティを **True** に設定するとエラー メッセージが表示されます。  これは、このような場合、Visual Studio が文書内の VBA プロジェクトを変更できないからです。  
  
5.  表示されたメッセージで **\[OK\]** をクリックします。  このメッセージは、プロジェクトを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] から実行するときに VBA コードをブックまたは文書に追加した場合、次にプロジェクトをビルドするときにその VBA コードが失われることを示します。  これは、プロジェクトをビルドするたびに、ビルド出力フォルダー内のブックまたは文書が上書きされるからです。  
  
     この時点で、Visual Studio によって、VBA プロジェクトがアセンブリを呼び出すことができるようにプロジェクトが構成されます。  さらに、Visual Studio は `CallVSTOAssembly` という名前のプロパティを VBA プロジェクトの `ThisDocument`、`ThisWorkbook`、`Sheet1`、`Sheet2`、または `Sheet3` モジュールに追加します。  このプロパティを使用して、VBA に公開したクラスのパブリック メンバーにアクセスできます。  
  
6.  プロジェクトをビルドします。  
  
##  <a name="NonHostItem"></a> ホスト項目クラスにはないコードを公開する  
 ホスト項目クラスにはない Visual Basic コードを VBA コードで呼び出すことができるようにするには、コードを変更して VBA から参照できるようにします。  
  
#### ホスト項目クラスにはないコードを VBA に公開するには  
  
1.  マクロをサポートする Word 文書、Excel ブック、または Excel テンプレートに基づく、VBA コードが既に含まれているドキュメント レベルの [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] プロジェクトを開くか、または作成します。  
  
     マクロをサポートするドキュメント ファイル形式の詳細については、「[VBA とドキュメント レベルのカスタマイズの結合](../vsto/combining-vba-and-document-level-customizations.md)」を参照してください。  
  
    > [!NOTE]  
    >  この機能は、Word テンプレート プロジェクトでは使用できません。  
  
2.  ドキュメント内の VBA コードがユーザーにマクロの有効化を要求することなく実行可能であることを確認します。  Word または Excel のセキュリティ センターの設定にある信頼できる場所の一覧に Office プロジェクトの場所を追加することで、VBA コードを信頼して実行できるようになります。  
  
3.  VBA に公開するメンバーをプロジェクトのパブリック クラスに追加し、そのメンバーを **public** として宣言します。  
  
4.  VBA に公開するクラスに次の <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性および <xref:Microsoft.VisualBasic.ComClassAttribute> 属性を適用します。  これらの属性によって、クラスが VBA から参照できるようになります。  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  プロジェクト内のホスト項目クラスの **GetAutomationObject** メソッドをオーバーライドして、VBA に公開するクラスのインスタンスを返します。  次のコード例では、`DocumentUtilities` という名前のクラスを VBA に公開することを前提としています。  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  文書 \(Word の場合\) またはワークシート \(Excel の場合\) を [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 内のデザイナーで開きます。  
  
7.  **\[プロパティ\]** ウィンドウで **ReferenceAssemblyFromVbaProject** プロパティを選択し、値を **True** に変更します。  
  
    > [!NOTE]  
    >  ブックまたは文書に VBA コードが含まれていない場合、または文書内の VBA コードに実行に対する信頼が付与されていない場合に、**ReferenceAssemblyFromVbaProject** プロパティを選択し、値を **True** に設定するとエラー メッセージが表示されます。  これは、このような場合、Visual Studio が文書内の VBA プロジェクトを変更できないからです。  
  
8.  表示されたメッセージで **\[OK\]** をクリックします。  このメッセージは、プロジェクトを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] から実行するときに VBA コードをブックまたは文書に追加した場合、次にプロジェクトをビルドするときにその VBA コードが失われることを示します。  これは、プロジェクトをビルドするたびに、ビルド出力フォルダー内のブックまたは文書が上書きされるからです。  
  
     この時点で、Visual Studio によって、VBA プロジェクトがアセンブリを呼び出すことができるようにプロジェクトが構成されます。  さらに、Visual Studio は `GetManagedClass` という名前のメソッドを VBA プロジェクトに追加します。  このメソッドは VBA プロジェクト内のどこからでも呼び出すことができ、それによって VBA に公開したクラスにアクセスできます。  
  
9. プロジェクトをビルドします。  
  
## 参照  
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [VBA とドキュメント レベルのカスタマイズの結合](../vsto/combining-vba-and-document-level-customizations.md)   
 [チュートリアル : VBA から Visual Basic プロジェクトのコードを呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [方法 : Visual C&#35; プロジェクトのコードを VBA に公開する](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  