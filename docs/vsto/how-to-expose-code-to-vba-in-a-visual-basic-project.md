---
title: "方法: Visual Basic プロジェクトでの vba コードに公開 |Microsoft ドキュメント"
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
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
ms.assetid: dc74f3ea-3f78-47f8-8a82-a67896144dd9
caps.latest.revision: "47"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 90f97a36b3293ad2e8f3c6ab046b500ab30d4c83
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>方法 : Visual Basic プロジェクトのコードを VBA に公開する
  内のコードを公開することができます、[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]プロジェクトの Visual Basic for Applications (VBA) コードする場合は相互にやり取りするコードの 2 つの種類。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Visual Basic のプロセスは、Visual c# のプロセスと異なります。 詳細については、次を参照してください[する方法: コードを Visual C &#35; VBA に公開。プロジェクト](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)です。  
  
 プロセスは、異なるホスト項目クラス内のコードは、他のクラス コードです。  
  
-   [ホスト項目クラスにコードを公開します。](#HostItemCode)  
  
-   [ホスト項目クラスに含まれていないコードを公開します。](#NonHostItem)  
  
 ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください。[方法は i: 呼び出す VSTO コードを VBA から?](http://go.microsoft.com/fwlink/?LinkId=136757)です。  
  
##  <a name="HostItemCode"></a>ホスト項目クラスにコードを公開します。  
 ホスト項目クラスの Visual Basic コードを呼び出す VBA コードを有効にするには設定、 **EnableVbaCallers**するホスト項目のプロパティ**True**です。  
  
 ホスト項目クラスのメソッドを公開し、VBA から呼び出す方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: Visual Basic プロジェクト内の VBA からのコードを呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)です。 ホスト項目の詳細については、「 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)」を参照してください。  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>コードを VBA にホスト項目を公開するには  
  
1.  ドキュメント レベルの作成を開いたり[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]に基づく Word 文書、Excel ブックまたは Excel テンプレートのマクロをサポートして、VBA コードを既に含むプロジェクトです。  
  
     マクロをサポートするドキュメントのファイル形式の詳細については、次を参照してください。[結合 VBA とドキュメント レベルのカスタマイズ](../vsto/combining-vba-and-document-level-customizations.md)です。  
  
    > [!NOTE]  
    >  この機能は、Word テンプレート プロジェクトでは使用できません。  
  
2.  ドキュメント内の VBA コードのマクロを有効にするユーザーに確認しないで実行が許可されることを確認します。 Word または Excel のセキュリティ センター設定の信頼できる場所の一覧に Office プロジェクトの場所を追加することによって、VBA コードの実行を信頼することができます。  
  
3.  プロパティ、メソッド、または、プロジェクトのホスト項目クラスのいずれかには、VBA に公開するイベントを追加し、新しいメンバーとして宣言**パブリック**です。 クラスの名前は、アプリケーションによって異なります。  
  
    -   Word プロジェクト、ホスト項目クラスの名前が`ThisDocument`既定です。  
  
    -   Excel プロジェクトでは、ホスト項目クラスには名前付き`ThisWorkbook`、 `Sheet1`、 `Sheet2`、および`Sheet3`既定です。  
  
4.  設定、 **EnableVbaCallers**にホスト項目プロパティを**True**です。 使用できる、このプロパティは、**プロパティ**ホスト項目は、デザイナーで開いているときにウィンドウです。  
  
     このプロパティを設定すると、Visual Studio が自動的に設定、 **ReferenceAssemblyFromVbaProject**プロパティを**True**です。  
  
    > [!NOTE]  
    >  かどうか、ブックまたはドキュメントが含まれない VBA コード、またはドキュメント内の VBA コードが実行を信頼されていない場合は、設定すると、エラー メッセージが表示されるが、 **EnableVbaCallers**プロパティを**True**です。 これは、このような状況では、Visual Studio がドキュメントのVBA プロジェクトを変更できないためです。  
  
5.  表示されるメッセージで **[OK]** をクリックします。 このメッセージは、ブックまたはドキュメントに VBA コードを追加する場合、プロジェクトからを実行して、知らせる[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、VBA コードは失われます次に、プロジェクトをビルドするとき。 これは、プロジェクトをビルドするたびに、ビルド出力フォルダー内のドキュメントが上書きされるためです。  
  
     この時点では、Visual Studio は VBA プロジェクトが、アセンブリを呼び出すことができるように、プロジェクトを構成します。 Visual Studio はという名前のプロパティも追加`CallVSTOAssembly`を`ThisDocument`、 `ThisWorkbook`、 `Sheet1`、 `Sheet2`、または`Sheet3`VBA プロジェクトのモジュール。 このプロパティを使用して、VBA に公開したクラスのパブリック メンバーにアクセスすることができます。  
  
6.  プロジェクトをビルドします。  
  
##  <a name="NonHostItem"></a>ホスト項目クラスに含まれていないコードを公開します。  
 ホスト項目クラスに含まれていない Visual Basic コードを呼び出す VBA コードを有効にするが VBA に見えるようにコードを変更します。  
  
#### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>コードを VBA にホスト項目クラスに含まれていないを公開するには  
  
1.  ドキュメント レベルの作成を開いたり[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]に基づく Word 文書、Excel ブックまたは Excel テンプレートのマクロをサポートして、VBA コードを既に含むプロジェクトです。  
  
     マクロをサポートするドキュメントのファイル形式の詳細については、次を参照してください。[結合 VBA とドキュメント レベルのカスタマイズ](../vsto/combining-vba-and-document-level-customizations.md)です。  
  
    > [!NOTE]  
    >  この機能は、Word テンプレート プロジェクトでは使用できません。  
  
2.  ドキュメント内の VBA コードのマクロを有効にするユーザーに確認しないで実行が許可されることを確認します。 Word または Excel のセキュリティ センター設定の信頼できる場所の一覧に Office プロジェクトの場所を追加することによって、VBA コードの実行を信頼することができます。  
  
3.  プロジェクト内のパブリック クラスを VBA に公開するメンバーを追加し、新しいメンバーとして宣言**パブリック**です。  
  
4.  次の適用<xref:System.Runtime.InteropServices.ComVisibleAttribute>と<xref:Microsoft.VisualBasic.ComClassAttribute>属性を VBA に公開したクラスにします。 これらの属性は、VBA に表示されるクラスを作成します。  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  プロジェクトでホスト項目クラスの **GetAutomationObject** メンバーをオーバーライドして、VBA に公開したクラスのインスタンスを返すようにします。 次のコード例は、という名前のクラスを公開することが前提としています。`DocumentUtilities`を VBA にします。  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  Word の場合) のドキュメントまたは (Excel) のワークシート デザイナーで開く[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]です。  
  
7.  **[プロパティ]** ウィンドウで、 **ReferenceAssemblyFromVbaProject** プロパティを選択し、値を **True**に変更します。  
  
    > [!NOTE]  
    >  かどうか、ブックまたはドキュメントが含まれない VBA コード、またはドキュメント内の VBA コードが実行を信頼されていない場合は、設定すると、エラー メッセージが表示されるが、 **ReferenceAssemblyFromVbaProject**プロパティを**は True。**. これは、このような状況では、Visual Studio がドキュメントのVBA プロジェクトを変更できないためです。  
  
8.  表示されるメッセージで **[OK]** をクリックします。 このメッセージは、ブックまたはドキュメントに VBA コードを追加する場合、プロジェクトからを実行して、知らせる[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、VBA コードは失われます次に、プロジェクトをビルドするとき。 これは、プロジェクトをビルドするたびに、ビルド出力フォルダー内のドキュメントが上書きされるためです。  
  
     この時点では、Visual Studio は VBA プロジェクトが、アセンブリを呼び出すことができるように、プロジェクトを構成します。 Visual Studio がという名前のメソッドを追加また`GetManagedClass`VBA プロジェクトにします。 どこからでもこのメソッドを呼び出すことができますを VBA に公開したクラスにアクセスする VBA プロジェクトにします。  
  
9. プロジェクトをビルドします。  
  
## <a name="see-also"></a>参照  
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [設計と、Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [Combining VBA and Document-Level Customizations](../vsto/combining-vba-and-document-level-customizations.md)   
 [チュートリアル: Visual Basic プロジェクトでの VBA からのコードの呼び出し](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [方法: Visual C &#35; での vba コードに公開プロジェクト](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
  
  