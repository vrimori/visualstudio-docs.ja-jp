---
title: リボン XML
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VSTO.Ribbon.RibbonXMLItem
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- callback methods
- custom Ribbon, displaying
- custom Ribbon, defining behavior
- XML [Office development in Visual Studio], Ribbon
- customizing the Ribbon, defining behavior
- Ribbon [Office development in Visual Studio], customizing
- customizing the Ribbon, displaying
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c93553535ca85f63db64be773afa76711a38359b
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693131"
---
# <a name="ribbon-xml"></a>リボン XML
  リボン (XML) 項目では、XML を使用してリボンをカスタマイズすることができます。 リボン (ビジュアル デザイナー) 項目でサポートされていない方法でリボンをカスタマイズする場合は、リボン (XML) 項目を使用します。 各項目で実行できる操作の比較を参照してください。[リボンの概要](../vsto/Ribbon-overview.md)です。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="add-a-ribbon-xml-item-to-a-project"></a>リボン (XML) 項目をプロジェクトに追加します。  
 **[新しい項目の追加]** ダイアログ ボックスから、 **リボン (XML)** 項目を任意の Office プロジェクトに追加できます。 Visual Studio によってプロジェクトに次のファイルが自動的に追加されます。  
  
-   リボン XML ファイル。 このファイルは、リボン ユーザー インターフェイス (UI) を定義します。 タブ、グループ、およびコントロールなどの UI 要素を追加するには、このファイルを使用します。 詳細については、「[リボン XML ファイル リファレンス](#RibbonDescriptorFile)このトピックで後述します。  
  
-   リボン コード ファイル。 このファイルには *リボン クラス*が含まれています。 このクラスの名前は、 **[新しい項目の追加]** ダイアログ ボックスで **リボン (XML)** 項目に指定した名前になります。 Microsoft Office アプリケーションでは、このクラスのインスタンスを使用して、カスタム リボンを読み込みます。 詳細については、「[クラス参照をリボン](#RibbonExtensionClass)このトピックで後述します。  
  
 既定では、これらのファイルはカスタム グループを追加、**アドイン**をリボンにタブです。  
  
## <a name="display-the-custom-ribbon-in-a-microsoft-office-application"></a>Microsoft Office アプリケーションにカスタム リボンを表示します。  
 追加した後、**リボン (XML)** 項目をプロジェクトにコードを追加する必要があります、 **ThisAddin**、 **ThisWorkbook**、または**ThisDocument**クラスオーバーライドする、`CreateRibbonExtensibilityObject`メソッド、リボン XML クラスを返す、Office アプリケーションにします。  
  
 次のコード例は `CreateRibbonExtensibilityObject` メソッドをオーバーライドして、MyRibbon という名前のリボン XML クラスを返します。  
  
 [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
 [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
## <a name="define-the-behavior-of-the-custom-ribbon"></a>カスタム リボンの動作を定義します。  
 作成することで、リボンのボタンをクリックするなどのユーザー アクションに応答できる*コールバック メソッド*です。 コールバック メソッドは Windows フォーム コントロールのイベントと似ていますが、UI 要素の XML の属性によって識別されます。 リボン クラスでメソッドを記述すると、コントロールは属性値と同じ名前を持つメソッドを呼び出します。 たとえば、ユーザーがリボン上のボタンをクリックしたときに呼び出されるコールバック メソッドを作成することができます。 コールバック メソッドを作成するには、2 つの手順が必要です。  
  
-   コード内のコールバック メソッドを識別するリボン XML ファイル内のコントロールに、属性を割り当てます。  
  
-   リボン クラスでコールバック メソッドを定義します。  
  
> [!NOTE]  
>  Outlook では追加の手順が必要です。 詳細については、次を参照してください。 [Outlook のリボンをカスタマイズ](../vsto/customizing-a-ribbon-for-outlook.md)です。  
  
 リボンからアプリケーションを自動化する方法について説明するチュートリアルでは、次を参照してください。[チュートリアル: リボン XML によるカスタム タブを作成](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)です。  
  
### <a name="assign-callback-methods-to-controls"></a>コントロールにコールバック メソッドを割り当てる  
 コールバック メソッドをリボン XML ファイル内のコントロールに割り当てるには、コールバック メソッドの種類とメソッドの名前を指定する属性を追加します。 たとえば、次の要素は **OnToggleButton1** という名前の `OnToggleButton1`」をご覧ください。  
  
```xml  
<toggleButton id="toggleButton1" onAction="OnToggleButton1" />  
```  
  
 **onAction** は、特定のコントロールに関連付けられている主なタスクをユーザーが実行すると呼び出されます。 たとえば、トグル ボタンの **onAction** コールバック メソッドは、ユーザーがボタンをクリックするとが呼び出されます。  
  
 属性で指定するメソッドは、どんな名前をつけてもかまいません。 ただし、その名前はリボンのコード ファイルで定義するメソッドの名前と一致する必要があります。  
  
 リボン コントロールに割り当てることができるコールバック メソッドにはさまざまな種類があります。 各コントロールの使用可能なコールバック メソッドの一覧については、技術記事を参照してください。[開発者 (パート 3/3) (2007 Office リボンのユーザー インターフェイスをカスタマイズ](http://msdn.microsoft.com/en-us/a16c7df5-93f3-4920-baa8-7b7290794c15)です。  
  
###  <a name="CallBackMethods"></a> コールバック メソッドを定義します。  
 リボン クラスのコールバック メソッドはリボン コード ファイルで定義します。 コールバック メソッドにはいくつかの要件があります。  
  
-   コールバック メソッドはパブリック メソッドとして宣言されなければなりません。  
  
-   コールバック メソッドの名前は、リボン XML ファイル内のコントロールに割り当てたコールバック メソッドの名前と一致する必要があります。  
  
-   コールバック メソッドのシグネチャは、関連付けられているリボン コントロールの利用可能なコールバック メソッドの型のシグネチャと一致する必要があります。  
  
 リボン コントロールのコールバック メソッドのシグネチャの完全な一覧は、技術記事を参照してください。[開発者 (パート 3/3) (2007 Office リボンのユーザー インターフェイスをカスタマイズ](http://msdn.microsoft.com/en-us/a16c7df5-93f3-4920-baa8-7b7290794c15)です。 Visual Studio では、リボン コード ファイルで作成するコールバック メソッドの IntelliSense サポートは提供されていません。 有効なシグネチャに一致しないコールバック メソッドを作成した場合、コードはコンパイルされますが、ユーザーがコントロールをクリックしても、何も起こりません。  
  
 すべてのコールバック メソッドには、メソッドを呼び出すコントロールを表す <xref:Microsoft.Office.Core.IRibbonControl> パラメーターがあります。 このパラメーターを使用して、同じコールバック メソッドを複数のコントロールで再利用できます。 次のコード例は、ユーザーがクリックするコントロールに応じて異なるタスクを実行する **onAction** コールバック メソッドを示しています。  
  
 [!code-csharp[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#2)]
 [!code-vb[Trin_RibbonOutlookBasic#2](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#2)]  
  
##  <a name="RibbonDescriptorFile"></a> リボン XML ファイル リファレンス  
 要素を追加して、属性により、カスタム リボンをリボン XML ファイルに定義できます。 既定では、リボン XML ファイルには次の XML が含まれています。  
  
```xml  
<?xml version="1.0" encoding="UTF-8"?>  
<customUI xmlns="http://schemas.microsoft.com/office/2006/01/customui" onLoad="OnLoad">  
  <ribbon>  
    <tabs>  
      <tab idMso="TabAddIns">  
        <group id="MyGroup"  
               label="My Group">  
        </group>  
      </tab>  
    </tabs>  
  </ribbon>  
</customUI>  
```  
  
 次の表は、リボン XML ファイルの既定の要素について説明しています。  
  
|要素|説明|  
|-------------|-----------------|  
|**customUI**|VSTO アドイン プロジェクトでのカスタム リボンを表します。|  
|**ribbon**|リボンを表します。|  
|**タブ**|[リボン] タブのセットを表します。|  
|**タブ**|単独の [リボン] タブを表します。|  
|**group**|[リボン] タブのコントロールのグループを表します。|  
  
 これらの要素には、カスタム リボンの動作と外観を指定する属性があります。 次の表は、リボン XML ファイルの既定の属性について説明しています。  
  
|属性|親要素|説明|  
|---------------|--------------------|-----------------|  
|**onLoad**|**customUI**|アプリケーションがリボンを読み込むときに呼び出されるメソッドを識別します。|  
|**idMso**|**タブ**|リボンに表示する組み込みタブを識別します。|  
|**ID**|**group**|グループを識別します。|  
|**label**|**group**|グループに表示するテキストを指定します。|  
  
 リボン XML ファイルの既定の要素と属性は、使用できる要素と属性の小さなサブセットです。 利用可能な要素と属性の完全な一覧は、技術記事を参照してください[開発者 (パート 2/3) (2007 Office リボンのユーザー インターフェイスをカスタマイズ](http://msdn.microsoft.com/en-us/6b904f55-525f-4520-9b81-a017db65657b)です。  
  
##  <a name="RibbonExtensionClass"></a> リボン クラスのリファレンス  
 Visual Studio は、リボン コード ファイルにリボン クラスを生成します。 このクラスには、リボン上のコントロールのコールバック メソッドを追加します。 このクラスは、 <xref:Microsoft.Office.Core.IRibbonExtensibility> インターフェイスを実装します。  
  
 次の表はこのクラスの既定のメソッドについて説明しています。  
  
|メソッド|説明|  
|------------|-----------------|  
|`GetCustomUI`|リボン XML ファイルの内容を返します。 Microsoft Office アプリケーションでは、カスタム リボンのユーザー インターフェイスを定義する XML 文字列を取得するには、このメソッドを呼び出します。 このメソッドは、 <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> メソッドを実装します。 **注:** `GetCustomUI`をリボン XML ファイルの内容を返すだけに実装する必要があります、VSTO アドインで初期化するために使用する必要がありますされません。 具体的には、 `GetCustomUI` の実装で、ダイアログ ボックスや他のウィンドウを表示しようとしてはいけません。 それ以外の場合、カスタム リボンが正しく動作しない可能性があります。 VSTO アドインを初期化するコードを実行する必要がある場合は、そのコードを `ThisAddIn_Startup` イベント ハンドラーに追加します。|  
|`OnLoad`|<xref:Microsoft.Office.Core.IRibbonControl> パラメーターを `Ribbon` フィールドに割り当てます。 Microsoft Office アプリケーションは、カスタム リボンが読み込まれるときに、このメソッドを呼び出します。 このフィールドは、カスタム リボンを動的に更新を使用することができます。 詳細については、技術記事を参照してください。[開発者 (パート 1/3) (2007 Office リボンのユーザー インターフェイスをカスタマイズ](http://msdn.microsoft.com/en-us/a4fd6d18-d4a8-4e64-bd89-f437208573d3)です。|  
|`GetResourceText`|`GetCustomUI` メソッドによって呼び出され、リボン XML ファイルの内容を取得します。|  
  
## <a name="see-also"></a>関連項目  
 [リボンの概要](../vsto/ribbon-overview.md)   
 [チュートリアル: リボン XML によるカスタム タブを作成します。](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [Office UI のカスタマイズ](../vsto/office-ui-customization.md)  
  
  