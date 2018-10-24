---
title: 他の Office ソリューションから VSTO アドイン内のコードを呼び出す
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7849f0df8f7e2f29c34b129dbf8e684424711b44
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904649"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>他の Office ソリューションから VSTO アドイン内のコードを呼び出す
  VSTO アドイン内のオブジェクトは、他の Microsoft Office ソリューションを含む、他のソリューションに公開できます。 このことは、VSTO アドインが他のソリューションで使用可能なサービスを含む場合に便利です。 たとえば、この場合は、Web サービスから受け取る財務データについて計算を実行する Microsoft Office Excel の VSTO アドインである場合は、その他のソリューションは実行時に Excel VSTO アドインを呼び出すことによってこれらの計算を実行できます。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 この処理には主に 2 つの手順があります。  
  
-   VSTO アドインで、オブジェクトを他のソリューションに公開します。  
  
-   もう 1 つのソリューションで、VSTO アドインにより公開されたオブジェクトにアクセスし、オブジェクトのメンバーを呼び出します。  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>アドインでコードを呼び出すことができるソリューションの種類  
 次の種類のソリューションに VSTO アドイン内のオブジェクトを公開することができます。  
  
-   VSTO アドインと同じアプリケーション プロセスに読み込まれるドキュメント内の Visual Basic for Applications (VBA) コード。  
  
-   VSTO アドインと同じアプリケーション プロセスに読み込まれるドキュメント レベルのカスタマイズ。  
  
-   Visual Studio に含まれる Office プロジェクト テンプレートを使用して作成された他の VSTO アドイン。  
  
-   COM VSTO アドイン (つまり、 <xref:Extensibility.IDTExtensibility2> インターフェイスを直接実装する VSTO アドイン)。  
  
-   VSTO アドインとは異なるプロセスで実行中の任意のソリューション (こうした種類のソリューションは *アウト プロセス クライアント*とも呼ばれます)。 これらには、Windows フォームまたはコンソール アプリケーションなど、Office アプリケーションを自動化するアプリケーションと、異なるプロセスに読み込まれる VSTO アドインが含まれます。  
  
## <a name="expose-objects-to-other-solutions"></a>他のソリューションにオブジェクトを公開  
 VSTO アドイン内のオブジェクトを他のソリューションに公開するには、VSTO アドインで次の手順を実行します。  
  
1.  他のソリューションに公開するクラスを定義します。  
  
2.  <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> クラスの `ThisAddIn` メソッドをオーバーライドします。 他のソリューションに公開するクラスのインスタンスを返します。  
  
### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>他のソリューションに公開するクラスを定義します。  
 少なくとも、公開するクラスはパブリックであり、 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性の設定は **true**であり、 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) インターフェイスを公開する必要があります。  
  
 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) インターフェイスを公開する推奨方法は以下の手順を実行することです。  
  
1. 他のソリューションに公開するメンバーを宣言するインターフェイスを定義します。 このインターフェイスは、VSTO アドイン プロジェクトで定義できます。 ただし、クラスを非 VBA ソリューションに公開する場合、このインターフェイスを別のクラス ライブラリ プロジェクトで定義することを推奨します。そうすることで、VSTO アドインを呼び出すソリューションは VSTO アドイン プロジェクトを参照することなく、インターフェイスを参照できます。  
  
2. 適用、 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 、このインターフェイスに属性し、この属性を設定して**true**します。  
  
3. クラスを変更して、このインターフェイスを実装します。  
  
4. 適用、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性をクラスと、この属性を設定、 **None**の値、<xref:System.Runtime.InteropServices.ClassInterfaceType>列挙体。  
  
5. このクラスをアウト プロセス クライアントに公開する場合に、次はも必要。  
  
   -   <xref:System.Runtime.InteropServices.StandardOleMarshalObject>からクラスを派生させます。 詳細については、次を参照してください。[クラスをアウト プロセス クライアントに公開](#outofproc)します。  
  
   -   インターフェイスを定義するプロジェクトで、 **[COM の相互運用機能に登録]** プロパティを設定します。 このプロパティは、事前バインディングを使用して VSTO アドインを呼び出せるにクライアントを有効にする場合にのみ必要です。  
  
   次のコード例は、他のソリューションによって呼び出し可能な `AddInUtilities` メソッドを持つ、 `ImportData` クラスを示します。 大きなチュートリアルのコンテキストでこのコードを表示するには、次を参照してください。[チュートリアル: VBA から VSTO アドイン内のコードを呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)します。  
  
   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="expose-classes-to-vba"></a>クラスを VBA に公開します。  
 上記の手順を実行すると、VBA コードはインターフェイス内で宣言するメソッドのみを呼び出すことができます。 VBA コードは、 <xref:System.Object>など、クラスが基本クラスから取得するメソッドを含め、クラス内の他のメソッドを呼び出すことはできません。  
  
 別の方法として公開することができます、 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)インターフェイスを設定して、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性の値 (autodispatch に対する) または AutoDual 値を<xref:System.Runtime.InteropServices.ClassInterfaceType>列挙体。 インターフェイスを公開する場合は、個別のインターフェイスでメソッドを宣言するはありません。 ただし、VBA コードは、 <xref:System.Object>など、基本クラスから取得されるメソッドを含め、クラス内の任意のパブリックおよび非静的メソッドを呼び出すことができます。 さらに、事前バインディングを使用するアウト プロセス クライアントはクラスを呼び出すことができません。  
  
###  <a name="outofproc"></a> クラスをアウト プロセス クライアントに公開します。  
 VSTO アドイン内のクラスをアウト プロセス クライアントに公開する場合、 <xref:System.Runtime.InteropServices.StandardOleMarshalObject> からクラスを派生させ、アウト プロセス クライアントが公開された VSTO アドイン オブジェクトを呼び出せるようにする必要があります。 そうしないと、アウト プロセス クライアントで公開されたオブジェクトのインスタンスを取得しようとしたとき、予期せずに失敗する可能性があります。  
  
 この失敗は、Office アプリケーションのオブジェクト モデルのすべての呼び出しは、メイン UI スレッドで行う必要がありますが、アウト プロセス クライアントから、オブジェクトへの呼び出しは、任意の RPC (リモート プロシージャ コール) スレッドに到達するためです。 .NET Framework における COM マーシャリング機構はスレッドを切り替えず、メイン UI スレッドではなく、受信 RPC スレッド上のオブジェクトに呼び出しをマーシャリングすることを試みます。 オブジェクトが <xref:System.Runtime.InteropServices.StandardOleMarshalObject>から派生するクラスのインスタンスである場合、オブジェクトへの受信呼び出しは、公開されたオブジェクトが作成されたスレッド、つまりホスト アプリケーションのメイン UI スレッドに自動的にマーシャリングされます。  
  
 Office ソリューションにおけるスレッドの使用に関する詳細については、次を参照してください。[のスレッドの Office でサポート](../vsto/threading-support-in-office.md)します。  
  
### <a name="override-the-requestcomaddinautomationservice-method"></a>RequestComAddInAutomationService メソッドをオーバーライドします。  
 次のコード例は、VSTO アドイン内の <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> クラスで `ThisAddIn` をオーバーライドする方法を示します。 この例ではという名前のクラスが定義されている`AddInUtilities`他のソリューションに公開します。 大きなチュートリアルのコンテキストでこのコードを表示するには、次を参照してください。[チュートリアル: VBA から VSTO アドイン内のコードを呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)します。  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 VSTO アドインが読み込まれると、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> メソッドを呼び出します。 ランタイムは、COMAddIn.Object プロパティに、返されたオブジェクトを割り当てます、 <xref:Microsoft.Office.Core.COMAddIn> VSTO アドインを表すオブジェクト。 この <xref:Microsoft.Office.Core.COMAddIn> オブジェクトは他の Office ソリューションおよび Office を自動化するソリューションで利用できます。  
  
## <a name="access-objects-from-other-solutions"></a>他のソリューションからオブジェクトにアクセス  
 VSTO アドインで公開されたオブジェクトを呼び出すには、クライアント ソリューションで以下の手順を実行します。  
  
1. 公開された VSTO アドインを表す <xref:Microsoft.Office.Core.COMAddIn> オブジェクトを取得します。 クライアントは、ホスト Office アプリケーションのオブジェクト モデル内の `Application.COMAddIns` プロパティを使用して、使用可能なすべての VSTO アドインにアクセスできます。  
  
2. COMAddIn.Object プロパティへのアクセス、<xref:Microsoft.Office.Core.COMAddIn>オブジェクト。 このプロパティは VSTO アドインから公開されたオブジェクトを返します。  
  
3. 公開されたオブジェクトのメンバーを呼び出します。  
  
   COMAddIn.Object プロパティの戻り値を使用する方法は VBA クライアントと非 VBA クライアントで異なります。 アウト プロセス クライアントの場合、可能性のある競合状態を避けるために追加のコードが必要です。  
  
### <a name="access-objects-from-vba-solutions"></a>VBA ソリューションからオブジェクトにアクセス  
 次のコード例では、VSTO アドインによって公開されるメソッドを呼び出す VBA を使用する方法を示します。 この VBA マクロは、という名前のメソッドを呼び出す`ImportData`という名前は、VSTO アドインで定義されている**ExcelImportData**します。 大きなチュートリアルのコンテキストでこのコードを表示するには、次を参照してください。[チュートリアル: VBA から VSTO アドイン内のコードを呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)します。  
  
```vb
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="access-objects-from-non-vba-solutions"></a>非 VBA ソリューションからオブジェクトにアクセス  
 非 VBA ソリューションでは、それを実装するインターフェイスに COMAddIn.Object プロパティ値をキャストする必要があり、インターフェイス オブジェクトで公開されたメソッドを呼び出すことができます。 次のコード例は、Visual Studio に含まれる Office Developer Tools を使用して作成された異なる VSTO アドインから `ImportData` メソッドを呼び出す方法を示します。  
  
```vb  
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")  
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _  
    addIn.Object, ExcelImportData.IAddInUtilities)  
utilities.ImportData()  
```  
  
```csharp  
object addInName = "ExcelImportData";  
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);  
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;  
utilities.ImportData();  
```  
  
 COMAddIn.Object プロパティの値をキャストしようとする場合、この例では、`AddInUtilities`クラスではなく、`IAddInUtilities`インターフェイス、コードがスローされます、<xref:System.InvalidCastException>します。  
  
## <a name="see-also"></a>関連項目  
 [VSTO アドインをプログラミングします。](../vsto/programming-vsto-add-ins.md)   
 [チュートリアル: は、VSTO アドインのコードを VBA から呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Office ソリューションを開発します。](../vsto/developing-office-solutions.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)   
 [機能拡張インターフェイスによる UI 機能をカスタマイズします。](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  
