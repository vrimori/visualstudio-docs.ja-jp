---
title: '方法: Visual Basic プロジェクトでのコードを VBA に公開します。'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2da62fa4c5fc79fc217c165746e9f1fd062d3461
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867313"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>方法: Visual Basic プロジェクトでのコードを VBA に公開します。
  内のコードを公開することができます、[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]相互作用するコードの 2 つの種類の場合、Visual basic for Applications (VBA) コード プロジェクトします。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Visual Basic のプロセスは、Visual c# プロセスからは異なります。 詳細については、「[方法 :Visual C での vba コードに公開&#35;プロジェクト](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)します。  
  
 他のクラス内のコードよりも、ホスト項目クラスにコードの異なるプロセス。  
  
- [ホスト項目クラスにコードを公開します。](#HostItemCode)  
  
- [ホスト項目クラスに含まれていないコードに公開します。](#NonHostItem)  
  
  ![ビデオへのリンク](../vsto/media/playvideo.gif "ビデオへのリンク")関連するビデオ デモについては、次を参照してください[How do i:。VBA から VSTO コードを呼び出しますか。](http://go.microsoft.com/fwlink/?LinkId=136757).  
  
##  <a name="HostItemCode"></a> ホスト項目クラスにコードを公開します。  
 ホスト項目クラスの Visual Basic コードを呼び出す VBA コードを有効にするには設定、 **EnableVbaCallers**するホスト項目のプロパティ**True**します。  
  
 ホスト項目クラスのメソッドを公開し、VBA から呼び出す方法について説明するチュートリアルでは、次を参照してください。[チュートリアル。Visual Basic プロジェクトでコードを VBA から呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)します。 ホスト項目の詳細については、次を参照してください。[ホスト項目とホスト コントロールの概要](../vsto/host-items-and-host-controls-overview.md)します。  
  
#### <a name="to-expose-code-in-a-host-item-to-vba"></a>コードを VBA にホスト項目に公開するには  
  
1.  ドキュメント レベルの作成を開いたり[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]Word 文書、Excel ブックまたは Excel テンプレート、マクロをサポートして、VBA コードを既に含むに基づいているプロジェクト。  
  
     マクロをサポートするドキュメントのファイル形式の詳細については、次を参照してください。[結合 VBA とドキュメント レベルのカスタマイズ](../vsto/combining-vba-and-document-level-customizations.md)します。  
  
    > [!NOTE]  
    >  この機能は、Word テンプレート プロジェクトでは使用できません。  
  
2.  ドキュメント内の VBA コードがマクロを有効にするユーザーを確認なしで実行を許可されていることを確認します。 Word または Excel のセキュリティ センター設定の信頼できる場所の一覧に Office プロジェクトの場所を追加することによって、VBA コードの実行を信頼することができます。  
  
3.  プロパティ、メソッド、またはプロジェクトで、ホスト項目クラスのいずれかには、VBA に公開するイベントを追加し、新しいメンバーとして宣言**パブリック**します。 クラスの名前は、アプリケーションによって異なります。  
  
    -   Word プロジェクトでは、ホスト項目クラスの名前は`ThisDocument`既定。  
  
    -   Excel プロジェクトでは、ホスト項目クラスの名前は`ThisWorkbook`、 `Sheet1`、 `Sheet2`、および`Sheet3`既定。  
  
4.  設定、 **EnableVbaCallers**にホスト項目のプロパティ**True**します。 このプロパティは、**プロパティ**ホスト項目は、デザイナーで開いているときにウィンドウ。  
  
     このプロパティを設定した後、Visual Studio は自動的に設定、 **ReferenceAssemblyFromVbaProject**プロパティを**True**します。  
  
    > [!NOTE]  
    >  かどうかは、ブックまたはドキュメントが含まれない VBA コード、またはドキュメント内の VBA コードが実行する信頼されていない場合は、設定すると、エラー メッセージが表示されるが、 **EnableVbaCallers**プロパティを**True**します。 これは、このような状況では、Visual Studio がドキュメントのVBA プロジェクトを変更できないためです。  
  
5.  表示されるメッセージで **[OK]** をクリックします。 このメッセージは、ブックまたはドキュメントに VBA コードを追加する場合からプロジェクトを実行しているを知らせる[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、VBA コードは失われます、次回プロジェクトをビルドします。 これは、プロジェクトをビルドするたびにビルド出力フォルダー内のドキュメントが上書きされるためです。  
  
     この時点では、VBA プロジェクトがアセンブリを呼び出すことができるように、Visual Studio は、プロジェクトを構成します。 Visual Studio では、という名前のプロパティも追加します`CallVSTOAssembly`を`ThisDocument`、 `ThisWorkbook`、 `Sheet1`、 `Sheet2`、または`Sheet3`VBA プロジェクトのモジュール。 このプロパティを使用して、VBA に公開したクラスのパブリック メンバーにアクセスすることができます。  
  
6.  プロジェクトをビルドします。  
  
##  <a name="NonHostItem"></a> ホスト項目クラスに含まれていないコードに公開します。  
 ホスト項目クラスには Visual Basic コードを呼び出す VBA コードを有効にするには、VBA に表示されるため、コードを変更します。  
  
### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>ホスト項目クラスを VBA に含まれていないコードを公開するには  
  
1.  ドキュメント レベルの作成を開いたり[!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]Word 文書、Excel ブックまたは Excel テンプレート、マクロをサポートして、VBA コードを既に含むに基づいているプロジェクト。  
  
     マクロをサポートするドキュメントのファイル形式の詳細については、次を参照してください。[結合 VBA とドキュメント レベルのカスタマイズ](../vsto/combining-vba-and-document-level-customizations.md)します。  
  
    > [!NOTE]  
    >  この機能は、Word テンプレート プロジェクトでは使用できません。  
  
2.  ドキュメント内の VBA コードがマクロを有効にするユーザーを確認なしで実行を許可されていることを確認します。 Word または Excel のセキュリティ センター設定の信頼できる場所の一覧に Office プロジェクトの場所を追加することによって、VBA コードの実行を信頼することができます。  
  
3.  プロジェクトで、パブリック クラスを VBA に公開するメンバーを追加し、新しいメンバーとして宣言**パブリック**します。  
  
4.  次の適用<xref:System.Runtime.InteropServices.ComVisibleAttribute>と<xref:Microsoft.VisualBasic.ComClassAttribute>属性を VBA に公開するクラス。 これらの属性ことによって、クラスを VBA に表示します。  
  
    ```vb  
    <Microsoft.VisualBasic.ComClass()> _  
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _  
    ```  
  
5.  プロジェクトでホスト項目クラスの **GetAutomationObject** メンバーをオーバーライドして、VBA に公開したクラスのインスタンスを返すようにします。 次のコード例は、という名前のクラスを公開することが前提としています。 `DocumentUtilities` VBA にします。  
  
    ```vb  
    Protected Overrides Function GetAutomationObject() As Object  
        Return New DocumentUtilities()  
    End Function  
    ```  
  
6.  (Word) のドキュメントまたは (Excel) 用のワークシート デザイナーで開く[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]します。  
  
7.  **[プロパティ]** ウィンドウで、 **ReferenceAssemblyFromVbaProject** プロパティを選択し、値を **True**に変更します。  
  
    > [!NOTE]  
    >  かどうかは、ブックまたはドキュメントが含まれない VBA コード、またはドキュメント内の VBA コードが実行する信頼されていない場合は、設定すると、エラー メッセージが表示されるが、 **ReferenceAssemblyFromVbaProject**プロパティを**は True。**. これは、このような状況では、Visual Studio がドキュメントのVBA プロジェクトを変更できないためです。  
  
8.  表示されるメッセージで **[OK]** をクリックします。 このメッセージは、ブックまたはドキュメントに VBA コードを追加する場合からプロジェクトを実行しているを知らせる[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]、VBA コードは失われます、次回プロジェクトをビルドします。 これは、プロジェクトをビルドするたびにビルド出力フォルダー内のドキュメントが上書きされるためです。  
  
     この時点では、VBA プロジェクトがアセンブリを呼び出すことができるように、Visual Studio は、プロジェクトを構成します。 Visual Studio では、という名前のメソッドも追加します`GetManagedClass`VBA プロジェクトにします。 このメソッドは、任意の場所から呼び出すことができますを VBA に公開したクラスにアクセスする VBA プロジェクトにします。  
  
9. プロジェクトをビルドします。  
  
## <a name="see-also"></a>関連項目  
 [方法: Visual Studio での Office プロジェクトを作成します。](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [設計および Office ソリューションの作成](../vsto/designing-and-creating-office-solutions.md)   
 [VBA とドキュメント レベルのカスタマイズを結合します。](../vsto/combining-vba-and-document-level-customizations.md)   
 [チュートリアル: Visual Basic プロジェクトでコードを VBA から呼び出す](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)   
 [方法: Visual C での vba コードに公開&#35;プロジェクト](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)  
