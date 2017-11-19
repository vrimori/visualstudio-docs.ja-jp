---
title: "他の Office ソリューションから VSTO アドインのコードを呼び出す |Microsoft ドキュメント"
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
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
ms.assetid: c1f16b4c-9291-49ed-9694-a83a37109612
caps.latest.revision: "54"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 38508a664ff94628dfd3fd5ec00eacb32fbb1187
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="calling-code-in-vsto-add-ins-from-other-office-solutions"></a>その他の Office ソリューションから VSTO アドインのコードを呼び出す
  VSTO アドイン内のオブジェクトは、他の Microsoft Office ソリューションを含む、他のソリューションに公開できます。 このことは、VSTO アドインが他のソリューションで使用可能なサービスを含む場合に便利です。 たとえば、Web サービスから受け取る財務データについて計算を実行する、Microsoft Office Excel 向けの VSTO アドインがある場合、他のソリューションは、実行時に Excel VSTO アドインを呼び出すことで、これらの計算を実行できます。  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
 この処理には主に 2 つの手順があります。  
  
-   VSTO アドインで、オブジェクトを他のソリューションに公開します。  
  
-   もう 1 つのソリューションで、VSTO アドインにより公開されたオブジェクトにアクセスし、オブジェクトのメンバーを呼び出します。  
  
## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>アドイン内のコードを呼び出すことができるソリューションの種類  
 VSTO アドイン内のオブジェクトは次の種類のソリューションに公開できます。  
  
-   VSTO アドインと同じアプリケーション プロセスに読み込まれるドキュメント内の Visual Basic for Applications (VBA) コード。  
  
-   VSTO アドインと同じアプリケーション プロセスに読み込まれるドキュメント レベルのカスタマイズ。  
  
-   Visual Studio に含まれる Office プロジェクト テンプレートを使用して作成された他の VSTO アドイン。  
  
-   COM VSTO アドイン (つまり、 <xref:Extensibility.IDTExtensibility2> インターフェイスを直接実装する VSTO アドイン)。  
  
-   VSTO アドインとは異なるプロセスで実行中の任意のソリューション (こうした種類のソリューションは *アウト プロセス クライアント*とも呼ばれます)。 これらには、Windows フォームまたはコンソール アプリケーションなど、Office アプリケーションを自動化するアプリケーションと、異なるプロセスに読み込まれる VSTO アドインが含まれます。  
  
## <a name="exposing-objects-to-other-solutions"></a>他のソリューションに対するオブジェクトの公開  
 VSTO アドイン内のオブジェクトを他のソリューションに公開するには、VSTO アドインで次の手順を実行します。  
  
1.  他のソリューションに公開するクラスを定義します。  
  
2.  <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> クラスの `ThisAddIn` メソッドをオーバーライドします。 他のソリューションに公開するクラスのインスタンスを返します。  
  
### <a name="defining-the-class-you-want-to-expose-to-other-solutions"></a>他のソリューションに公開するクラスの定義  
 少なくとも、公開するクラスはパブリックであり、 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 属性の設定は **true**であり、 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) インターフェイスを公開する必要があります。  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) インターフェイスを公開する推奨方法は以下の手順を実行することです。  
  
1.  他のソリューションに公開するメンバーを宣言するインターフェイスを定義します。 このインターフェイスは、VSTO アドイン プロジェクトで定義できます。 ただし、クラスを非 VBA ソリューションに公開する場合、このインターフェイスを別のクラス ライブラリ プロジェクトで定義することを推奨します。そうすることで、VSTO アドインを呼び出すソリューションは VSTO アドイン プロジェクトを参照することなく、インターフェイスを参照できます。  
  
2.  適用、<xref:System.Runtime.InteropServices.ComVisibleAttribute>属性をこのインターフェイスに、この属性を設定および**true**です。  
  
3.  クラスを変更して、このインターフェイスを実装します。  
  
4.  適用、 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 、クラスに属性をこの属性を [なし] に設定の値、<xref:System.Runtime.InteropServices.ClassInterfaceType>列挙します。  
  
5.  クラスをアウト プロセス クライアントに公開する場合、以下の手順も実行する必要がある可能性があります。  
  
    -   <xref:System.Runtime.InteropServices.StandardOleMarshalObject>からクラスを派生させます。 詳細については、「 [アウト プロセス クライアントに対するクラスの公開](#outofproc)」を参照してください。  
  
    -   インターフェイスを定義するプロジェクトで、 **[COM の相互運用機能に登録]** プロパティを設定します。 これは、クライアントが事前バインディングを使用して VSTO アドインを呼び出せるようにする場合にのみ必要です。  
  
 次のコード例は、他のソリューションによって呼び出し可能な `AddInUtilities` メソッドを持つ、 `ImportData` クラスを示します。 大きなチュートリアルのコンテキストでこのコードを参照してください[チュートリアル: VBA から VSTO アドインでのコードを呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)です。  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
 [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]  
  
### <a name="exposing-classes-to-vba"></a>VBA に対するクラスの公開  
 上記の手順を実行すると、VBA コードはインターフェイス内で宣言するメソッドのみを呼び出すことができます。 VBA コードは、 <xref:System.Object>など、クラスが基本クラスから取得するメソッドを含め、クラス内の他のメソッドを呼び出すことはできません。  
  
 代わりに公開することができます、 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)インターフェイスを設定して、<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>属性の値 (autodispatch に対する) または AutoDual 値を<xref:System.Runtime.InteropServices.ClassInterfaceType>列挙します。 これを実行した場合、メソッドを別のインターフェイスで宣言する必要はありません。 ただし、VBA コードは、 <xref:System.Object>など、基本クラスから取得されるメソッドを含め、クラス内の任意のパブリックおよび非静的メソッドを呼び出すことができます。 さらに、事前バインディングを使用するアウト プロセス クライアントはクラスを呼び出すことができません。  
  
###  <a name="outofproc"></a> アウト プロセス クライアントに対するクラスの公開  
 VSTO アドイン内のクラスをアウト プロセス クライアントに公開する場合、 <xref:System.Runtime.InteropServices.StandardOleMarshalObject> からクラスを派生させ、アウト プロセス クライアントが公開された VSTO アドイン オブジェクトを呼び出せるようにする必要があります。 そうしないと、アウト プロセス クライアントで公開されたオブジェクトのインスタンスを取得しようとしたとき、予期せずに失敗する可能性があります。  
  
 これは、Office アプリケーションのオブジェクト モデルのすべての呼び出しはメイン UI スレッド上で実行される必要があるのに対して、アウト プロセス クライアントからオブジェクトへの呼び出しは任意の RPC (リモート プロシージャ コール) スレッドに到着するからです。 .NET Framework における COM マーシャリング機構はスレッドを切り替えず、メイン UI スレッドではなく、受信 RPC スレッド上のオブジェクトに呼び出しをマーシャリングすることを試みます。 オブジェクトが <xref:System.Runtime.InteropServices.StandardOleMarshalObject>から派生するクラスのインスタンスである場合、オブジェクトへの受信呼び出しは、公開されたオブジェクトが作成されたスレッド、つまりホスト アプリケーションのメイン UI スレッドに自動的にマーシャリングされます。  
  
 Office ソリューションにおけるスレッドの使用法の詳細については、「 [Threading Support in Office](../vsto/threading-support-in-office.md)」を参照してください。  
  
### <a name="overriding-the-requestcomaddinautomationservice-method"></a>RequestComAddInAutomationService メソッドのオーバーライド  
 次のコード例は、VSTO アドイン内の <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> クラスで `ThisAddIn` を無視する方法を示します。 この例では、他のソリューションに公開する `AddInUtilities` という名前のクラスを定義済みであると仮定しています。 大きなチュートリアルのコンテキストでこのコードを参照してください[チュートリアル: VBA から VSTO アドインでのコードを呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)です。  
  
 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]  
  
 VSTO アドインが読み込まれると、 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] は <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> メソッドを呼び出します。 ランタイムは返されるオブジェクトを、VSTO アドインを表す <xref:Microsoft.Office.Core.COMAddIn.Object%2A> オブジェクトの <xref:Microsoft.Office.Core.COMAddIn> プロパティに割り当てます。 この <xref:Microsoft.Office.Core.COMAddIn> オブジェクトは他の Office ソリューションおよび Office を自動化するソリューションで利用できます。  
  
## <a name="accessing-objects-from-other-solutions"></a>他のソリューションからのオブジェクトのアクセス  
 VSTO アドインで公開されたオブジェクトを呼び出すには、クライアント ソリューションで以下の手順を実行します。  
  
1.  公開された VSTO アドインを表す <xref:Microsoft.Office.Core.COMAddIn> オブジェクトを取得します。 クライアントは、ホスト Office アプリケーションのオブジェクト モデルで Application.COMAddIns プロパティを使用して、使用できる VSTO アドインのすべてをアクセスできます。  
  
2.  <xref:Microsoft.Office.Core.COMAddIn.Object%2A> オブジェクトの <xref:Microsoft.Office.Core.COMAddIn> プロパティにアクセスします。 このプロパティは VSTO アドインから公開されたオブジェクトを返します。  
  
3.  公開されたオブジェクトのメンバーを呼び出します。  
  
 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> プロパティの戻り値を使用する方法は VBA クライアントと 非VBA クライアントで異なります。 アウト プロセス クライアントの場合、可能性のある競合状態を避けるために追加のコードが必要です。  
  
### <a name="accessing-objects-from-vba-solutions"></a>VBA ソリューションからのオブジェクトのアクセス  
 次のコード例は、VBA を使用して、VSTO アドインにより公開されたメソッドを呼び出す方法を示します。 この VBA マクロは、 `ImportData` ExcelImportData **という名前の VSTO アドインで定義される**という名前のメソッドを呼び出します。 大きなチュートリアルのコンテキストでこのコードを参照してください[チュートリアル: VBA から VSTO アドインでのコードを呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)です。  
  
```  
Sub CallVSTOMethod()  
    Dim addIn As COMAddIn  
    Dim automationObject As Object  
    Set addIn = Application.COMAddIns("ExcelImportData")  
    Set automationObject = addIn.Object  
    automationObject.ImportData  
End Sub  
```  
  
### <a name="accessing-objects-from-non-vba-solutions"></a>非 VBA ソリューションからのオブジェクトのアクセス  
 非 VBA ソリューションでは、それが実装するインターフェイスに <xref:Microsoft.Office.Core.COMAddIn.Object%2A> プロパティ値をキャストする必要があり、その後、インターフェイス オブジェクト上で公開されたメソッドを呼び出すことができます。 次のコード例は、Visual Studio に含まれる Office Developer Tools を使用して作成された異なる VSTO アドインから `ImportData` メソッドを呼び出す方法を示します。  
  
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
  
 この例で、 <xref:Microsoft.Office.Core.COMAddIn.Object%2A> プロパティの値を `AddInUtilities` インターフェイスではなく `IAddInUtilities` クラスにキャストしようとすると、コードは <xref:System.InvalidCastException>をスローします。  
  
## <a name="see-also"></a>関連項目  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [チュートリアル: は、VSTO アドインのコードを VBA から呼び出す](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)   
 [Office ソリューションの開発](../vsto/developing-office-solutions.md)   
 [方法: Visual Studio での Office プロジェクトの作成](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [VSTO アドインのアーキテクチャ](../vsto/architecture-of-vsto-add-ins.md)   
 [機能拡張インターフェイスによる UI 機能のカスタマイズ](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)  
  
  