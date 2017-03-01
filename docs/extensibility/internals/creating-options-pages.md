---
title: "オプション ページを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed package framework, creating Tools Options pages
- Tools Options pages [Visual Studio SDK], creating using managed package framework
ms.assetid: 1bf11fec-dece-4943-8053-6de1483c43eb
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 56a51aa0a2232ff149e1959842fced1dc26e7c1b
ms.lasthandoff: 02/22/2017

---
# <a name="creating-options-pages"></a>[オプション] ページを作成します。
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]マネージ パッケージ フレームワークから派生したクラス<xref:Microsoft.VisualStudio.Shell.DialogPage>拡張、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を追加して IDE**オプション**ページを下にある、**ツール**メニュー</xref:Microsoft.VisualStudio.Shell.DialogPage> 。  
  
 実装するオブジェクト、指定した**ツール オプション**ページが、固有の Vspackage を関連付け、<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>オブジェクト</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>。  
  
 環境は、特定の実装しているオブジェクトをインスタンス化するため**ツール オプション** ページの IDE で特定のページが表示されます。  
  
-   A**ツール オプション**独自のオブジェクトにし、VSPackage を実装するオブジェクトではなく、ページを実装する必要があります。  
  
-   オブジェクトは、複数を実装できない**ツール オプション**ページです。  
  
## <a name="registering-as-a-tools-options-page-provider"></a>ツール オプション ページ プロバイダーとして登録します。  
 による VSPackage サポート ユーザー構成**ツール オプション**ページが提供するオブジェクトを示す**ツール オプション**のインスタンスを適用することでページ<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>に適用される、<xref:Microsoft.VisualStudio.Shell.Package>実装</xref:Microsoft.VisualStudio.Shell.Package></xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>。  
  
 1 つのインスタンスが存在する必要があります<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>のすべて<xref:Microsoft.VisualStudio.Shell.DialogPage>-派生型を実装する、**ツール オプション**ページ</xref:Microsoft.VisualStudio.Shell.DialogPage></xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>。  
  
 各インスタンス<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>を実装する型を使用して、**ツール オプション** ページのカテゴリとサブカテゴリを識別するために使用を含む文字列、**ツール オプション**ページ、およびリソース情報を提供すると、種類を登録する、**ツール オプション**ページ</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>。  
  
## <a name="persisting-tools-options-page-state"></a>ツール オプション ページ状態の保持  
 場合、**ツール オプション**ページの実装が有効になっているオートメーションのサポートに登録されていると、IDE と共に他のすべてのページの状態を保持する**ツール オプション**ページです。  
  
 VSPackage は<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>。</xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>を使用して、独自の永続化を管理することができます。 1 つだけ、または永続化の他のメソッドを使用してください。  
  
## <a name="implementing-dialogpage-class"></a>DialogPage クラスを実装します。  
 VSPackage の実装を提供するオブジェクト、 <xref:Microsoft.VisualStudio.Shell.DialogPage>-派生型が次の継承された機能の活用:</xref:Microsoft.VisualStudio.Shell.DialogPage>  
  
-   既定のユーザー インターフェイス ウィンドウです。  
  
-   A 既定の永続化メカニズムが使用可能な場合<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラスに適用される場合は、<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>プロパティに設定されて`true`<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>クラスに適用されている</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>に関する</xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A></xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>  
  
-   オートメーションをサポートします。  
  
 実装するオブジェクトの最小要件、**ツール オプション**ページを使用して<xref:Microsoft.VisualStudio.Shell.DialogPage>のパブリック プロパティの追加は、</xref:Microsoft.VisualStudio.Shell.DialogPage> 。  
  
 としてクラスが正しく登録されている場合、**ツール オプション**そのパブリック プロパティが 利用可能なプロバイダーをページ、**オプション**のセクションで、**ツール**プロパティ グリッドのフォームのメニュー。  
  
 これらすべての既定の機能を無効にできます。 たとえば、作成するより高度なユーザー インターフェイスに必要のみ<xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>。</xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>の既定の実装をオーバーライドします。  
  
## <a name="example"></a>例  
 オプション ページの単純な"hello world"実装を次に示します。 既定のプロジェクトに次のコードを追加すると、Visual Studio パッケージ テンプレートによって作成された、**メニュー コマンド**オプションを選択したオプション ページの機能をデモンストレーション適切にします。  
  
### <a name="description"></a>説明  
 次のクラスでは、最小限の"hello world"のオプション ページを定義します。 ユーザーがパブリックに設定できる開かれると、`HelloWorld`プロパティ グリッド内のプロパティです。  
  
### <a name="code"></a>コード  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#11;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>説明  
 パッケージ クラスに次の属性を適用する ページのオプション使用できるように、パッケージの読み込み時にします。 番号は以下のカテゴリと、ページの任意のリソース Id を最後にブール値は、ページがオートメーションをサポートしているかどうかを指定します。  
  
### <a name="code"></a>コード  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#07;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>説明  
 次のイベント ハンドラーには、[オプション] ページで設定のプロパティの値に応じて結果が表示されます。 使用して、<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>ページによって公開されるプロパティにアクセスする、カスタム オプション ページの種類に結果を持つメソッドを明示的にキャストします</xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>。  
  
 パッケージ テンプレートによって生成されたプロジェクトの場合に、この関数からを呼び出す、`MenuItemCallback`に既定のコマンドにアタッチする機能が追加された、**ツール**メニュー。  
  
### <a name="code"></a>コード  
 [!code-cs[UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] 
 [!code-vb [UI_UserSettings_ToolsOptionPages&#08;](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [ユーザー設定の拡張とオプション](../../extensibility/extending-user-settings-and-options.md)   
 [オートメーション [オプション] ページのサポート](../../extensibility/internals/automation-support-for-options-pages.md)
