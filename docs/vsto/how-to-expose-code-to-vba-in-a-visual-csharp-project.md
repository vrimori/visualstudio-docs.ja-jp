---
title: "方法 : Visual C# プロジェクトのコードを VBA に公開する"
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
  - "VBA [Visual Studio での Office 開発], 公開 (ドキュメント レベルのカスタマイズ内のコードを)"
  - "Visual C# [Visual Studio での Office 開発], 公開 (コードを VBA に)"
ms.assetid: 56d5894b-4823-42f4-8c7e-d8739b859c52
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 方法 : Visual C# プロジェクトのコードを VBA に公開する
  2 種類のコードを連携させる場合は、Visual C\# プロジェクトのコードを Visual Basic for Applications \(VBA\) コードに公開することができます。  
  
 Visual C\# プロセスは Visual Basic プロセスとは異なります。  詳細については、「[方法 : Visual Basic プロジェクトのコードを VBA に公開する](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)」を参照してください。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Visual C\# プロジェクトのコードの公開  
 VBA コードから Visual C\# プロジェクトのコードを呼び出すには、VBA コードを変更して COM から参照できるようにし、デザイナーで **ReferenceAssemblyFromVbaProject** プロパティを **True** に設定します。  
  
 VBA から Visual C\# プロジェクト内のメソッドを呼び出す方法について説明したチュートリアルについては、「[チュートリアル : VBA から Visual C&#35; プロジェクトのコードを呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)」を参照してください。  
  
#### Visual C\# プロジェクトのコードを VBA に公開するには  
  
1.  マクロをサポートする Word 文書、Excel ブック、または Excel テンプレートに基づく、VBA コードが既に含まれているドキュメント レベルのプロジェクトを開くか、または作成します。  
  
     マクロをサポートするドキュメント ファイル形式の詳細については、「[VBA とドキュメント レベルのカスタマイズの結合](../vsto/combining-vba-and-document-level-customizations.md)」を参照してください。  
  
    > [!NOTE]  
    >  この機能は、Word テンプレート プロジェクトでは使用できません。  
  
2.  ドキュメント内の VBA コードがユーザーにマクロの有効化を要求することなく実行可能であることを確認します。  Word または Excel のセキュリティ センターの設定にある信頼できる場所の一覧に Office プロジェクトの場所を追加することで、VBA コードを信頼して実行できるようになります。  
  
3.  VBA に公開するメンバーをプロジェクトのパブリック クラスに追加し、そのメンバーを **public** として宣言します。  
  
4.  VBA に公開するクラスに次の <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性および <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 属性を適用します。  これらの属性によって、クラス インターフェイスを生成しなくても VBA に公開するクラスが COM から参照できるようになります。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  プロジェクトのホスト項目クラスの **GetAutomationObject** メソッドをオーバーライドして、VBA に公開するクラスのインスタンスを返します。  
  
    -   VBA にホスト項目クラスを公開する場合は、このクラスに属する **GetAutomationObject** メソッドをオーバーライドし、このクラスの現在のインスタンスを返します。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   VBA にホスト項目ではないクラスを公開する場合は、プロジェクト内のいずれかのホスト項目に属する **GetAutomationObject** メソッドをオーバーライドし、ホスト項目ではないクラスのインスタンスを返します。  たとえば、次のコードでは、`DocumentUtilities` という名前のクラスを VBA に公開することを前提としています。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     ホスト項目の詳細については、「[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
6.  VBA に公開するクラスからインターフェイスを抽出します。  **\[インターフェイスの公開\]** ダイアログ ボックスで、インターフェイス宣言に含めるパブリック メンバーを選択します。  詳細については、「[Extract Interface Refactoring &#40;C&#35;&#41;](../csharp-ide/extract-interface-refactoring-csharp.md)」を参照してください。  
  
7.  インターフェイス宣言に **public** キーワードを追加します。  
  
8.  インターフェイスに <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性を追加して、インターフェイスを COM から参照できるようにします。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. 文書 \(Word の場合\) またはワークシート \(Excel の場合\) を [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 内のデザイナーで開きます。  
  
10. **\[プロパティ\]** ウィンドウで **ReferenceAssemblyFromVbaProject** プロパティを選択し、値を **True** に変更します。  
  
    > [!NOTE]  
    >  ブックまたは文書に VBA コードが含まれていない場合、または文書内の VBA コードに実行に対する信頼が付与されていない場合は、**\[ReferenceAssemblyFromVbaProject\]** プロパティを選択し、値を **True** に設定するときにエラー メッセージが表示されます。  これは、このような場合、Visual Studio が文書内の VBA プロジェクトを変更できないからです。  
  
11. 表示されたメッセージで **\[OK\]** をクリックします。  このメッセージは、プロジェクトを [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] から実行するときに VBA コードをブックまたは文書に追加した場合、次にプロジェクトをビルドするときにその VBA コードが失われることを示します。  これは、プロジェクトをビルドするたびに、ビルド出力フォルダー内のブックまたは文書が上書きされるためです。  
  
     この時点で、Visual Studio によって、VBA プロジェクトがアセンブリを呼び出すことができるようにプロジェクトが構成されます。  さらに、Visual Studio は `GetManagedClass` という名前のメソッドを VBA プロジェクトに追加します。  このメソッドは VBA プロジェクト内のどこからでも呼び出すことができ、それによって VBA に公開したクラスにアクセスできます。  
  
12. プロジェクトをビルドします。  
  
## 参照  
 [方法: Visual Studio で Office プロジェクトを作成する](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Office ソリューションのデザインと作成](../vsto/designing-and-creating-office-solutions.md)   
 [VBA とドキュメント レベルのカスタマイズの結合](../vsto/combining-vba-and-document-level-customizations.md)   
 [チュートリアル : VBA から Visual C&#35; プロジェクトのコードを呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [方法 : Visual Basic プロジェクトのコードを VBA に公開する](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  