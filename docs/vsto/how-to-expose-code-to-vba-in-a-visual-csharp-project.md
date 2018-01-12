---
title: "方法: Visual c# プロジェクト内の vba コードに公開 |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: a4794f1cde57f365ec4ec98251763e8d0e839ae0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>方法 : Visual C# プロジェクトのコードを VBA に公開する
  相互にやり取りするコードの 2 つの種類の場合は、Visual c# プロジェクトを Visual Basic for Applications (VBA) コード内のコードを公開できます。  
  
 Visual c# のプロセスは、Visual Basic のプロセスと異なります。 詳細については、次を参照してください。[する方法: Visual Basic プロジェクトでは、VBA に公開コード](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)です。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## <a name="exposing-code-in-a-visual-c-project"></a>Visual c# プロジェクトでコードを公開します。  
 Visual c# プロジェクトのコードを呼び出す VBA コードを有効にするのには、COM から参照できるようにコードを変更し、設定、 **ReferenceAssemblyFromVbaProject**プロパティを**True**デザイナーでします。  
  
 VBA から Visual c# プロジェクトでメソッドを呼び出す方法を説明するチュートリアルでは、次を参照してください[チュートリアル: Visual C &#35; での VBA からのコードを呼び出す。プロジェクト](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)です。  
  
#### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>VBA を Visual c# プロジェクト内のコードを公開するには  
  
1.  開くか、Word 文書、Excel ブックまたは Excel テンプレートのマクロをサポートして、VBA コードを既に含むに基づいてドキュメント レベルのプロジェクトを作成します。  
  
     マクロをサポートするドキュメントのファイル形式の詳細については、次を参照してください。[結合 VBA とドキュメント レベルのカスタマイズ](../vsto/combining-vba-and-document-level-customizations.md)です。  
  
    > [!NOTE]  
    >  この機能は、Word テンプレート プロジェクトでは使用できません。  
  
2.  ドキュメント内の VBA コードのマクロを有効にするユーザーに確認しないで実行が許可されることを確認します。 Word または Excel のセキュリティ センター設定の信頼できる場所の一覧に Office プロジェクトの場所を追加することによって、VBA コードの実行を信頼することができます。  
  
3.  プロジェクト内のパブリック クラスを VBA に公開するメンバーを追加し、新しいメンバーとして宣言**パブリック**です。  
  
4.  次の適用<xref:System.Runtime.InteropServices.ComVisibleAttribute>と<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性を VBA に公開したクラスにします。 これらの属性によってクラスが COM で表示されるようになりますが、クラスのインターフェイスは生成されません。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    [System.Runtime.InteropServices.ClassInterface(  
        System.Runtime.InteropServices.ClassInterfaceType.None)]  
    ```  
  
5.  上書き、 **GetAutomationObject**を VBA に公開したクラスのインスタンスを返す、プロジェクトでホスト項目クラスのメソッド。  
  
    -   VBA にホスト項目クラスを公開する場合は、上書き、 **GetAutomationObject**このクラスに属しているクラスの現在のインスタンスを返すメソッド。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return this;  
        }  
        ```  
  
    -   クラスを VBA にホスト項目ではないことを公開する場合の上書き、 **GetAutomationObject**任意のホストのメソッドが、プロジェクト内の項目を非ホスト項目クラスのインスタンスを返します。 たとえば、次のコードはという名前のクラスを公開することを仮定`DocumentUtilities`を VBA にします。  
  
        ```csharp  
        protected override object GetAutomationObject()  
        {  
            return new DocumentUtilities();  
        }  
        ```  
  
     ホスト項目の詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
6.  クラスを VBA に公開するインターフェイスを抽出します。 **インターフェイスの抽出** ダイアログ ボックスで、インターフェイスの宣言に追加するパブリック メンバーを選択します。 詳細については、次を参照してください。[インターフェイスの抽出リファクタリング (&) #40 です。C# 35; &#41;](/visualstudio/csharp-ide/extract-interface-refactoring-csharp).  
  
7.  追加、**パブリック**キーワードをインターフェイスの宣言にします。  
  
8.  次を追加することで、インターフェイスを COM から参照できるように<xref:System.Runtime.InteropServices.ComVisibleAttribute>属性をインターフェイスです。  
  
    ```csharp  
    [System.Runtime.InteropServices.ComVisible(true)]  
    ```  
  
9. Word の場合) の文書またはワークシート (for Excel) をデザイナーで開く[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
10. **[プロパティ]** ウィンドウで、 **ReferenceAssemblyFromVbaProject** プロパティを選択し、値を **True**に変更します。  
  
    > [!NOTE]  
    >  ブックまたはドキュメントが含まれない VBA コードか、ドキュメント内の VBA コードが実行を信頼されていない場合は、設定すると、エラー メッセージが表示されるが、 **ReferenceAssemblyFromVbaProject**プロパティを**はTrue**. これは、このような状況では、Visual Studio がドキュメントのVBA プロジェクトを変更できないためです。  
  
11. 表示されるメッセージで **[OK]** をクリックします。 このメッセージを連絡することを追加する場合 VBA コードをブックまたはドキュメントからプロジェクトを実行するときに[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、VBA コードは失われます、次回、プロジェクトをビルドします。 ビルド内のドキュメントを出力フォルダーには、プロジェクトをビルドするたびには上書きされるためです。  
  
     この時点では、Visual Studio は VBA プロジェクトが、アセンブリを呼び出すことができるように、プロジェクトを構成します。 Visual Studio がという名前のメソッドを追加また`GetManagedClass`VBA プロジェクトにします。 どこからでもこのメソッドを呼び出すことができますを VBA に公開したクラスにアクセスする VBA プロジェクトにします。  
  
12. プロジェクトをビルドします。  
  
## <a name="see-also"></a>参照  
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [Visual C &#35; での VBA から呼び出すコードをチュートリアル:プロジェクト](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)   
 [方法: Visual Basic プロジェクトのコードを VBA に公開する](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)  
  
  