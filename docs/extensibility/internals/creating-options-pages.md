---
title: "オプション ページの作成 |Microsoft ドキュメント"
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
ms.translationtype: MT
ms.sourcegitcommit: eb5c9550fd29b0e98bf63a7240737da4f13f3249
ms.openlocfilehash: 6ed61dbc745b00f5f6f0beeba5aa38c3d316f98f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/06/2017

---
# <a name="creating-options-pages"></a>[オプション] ページを作成します。
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Managed package framework から派生したクラス<xref:Microsoft.VisualStudio.Shell.DialogPage>拡張、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]追加することによって IDE**オプション**ページの下にある、**ツール**メニュー。  
  
 実装するオブジェクト、指定された**ツール オプション**ページが、特定の Vspackage を関連付け、<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>オブジェクト。  
  
 環境が特定の実装しているオブジェクトをインスタンス化するため**ツール オプション**ページ、IDE によって特定のページを表示する場合。  
  
-   A**ツール オプション**独自のオブジェクトと、VSPackage を実装するオブジェクトではなく、ページを実装する必要があります。  
  
-   オブジェクトが複数を実装できません**ツール オプション**ページ。  
  
## <a name="registering-as-a-tools-options-page-provider"></a>ツール オプション ページ プロバイダーとして登録します。  
 VSPackage サポート ユーザーを使って構成**ツール オプション**ページが提供するオブジェクトを示す**ツール オプション**のインスタンスを適用することによってページ<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>に適用される<xref:Microsoft.VisualStudio.Shell.Package>実装します。  
  
 1 つのインスタンスである必要があります<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>のすべて<xref:Microsoft.VisualStudio.Shell.DialogPage>-派生型を実装する、**ツール オプション**ページ。  
  
 各インスタンス<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>を実装する型を使用して、**ツール オプション**ページで、カテゴリとサブカテゴリの識別に使用を含む文字列、**ツール オプション**ページ、およびリソース情報を提供すると、種類を登録する、**ツール オプション**ページ。  
  
## <a name="persisting-tools-options-page-state"></a>ツール オプション ページの状態を保持します。  
 場合、**ツール オプション**オートメーションのサポートが有効になっているページの実装が登録されている、IDE と共に他のすべてのページの状態が引き続き発生する**ツール オプション**ページ。  
  
 VSPackage を使用して、独自の永続化を管理できます<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>です。 1 つだけ、または永続化の他のメソッドを使用してください。  
  
## <a name="implementing-dialogpage-class"></a>DialogPage クラスの実装  
 VSPackage の実装を提供するオブジェクト、 <xref:Microsoft.VisualStudio.Shell.DialogPage>-派生型は次の継承された機能を利用できます。  
  
-   既定のユーザー インターフェイス ウィンドウです。  
  
-   A 既定の永続化メカニズムを使用可能な場合<xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>クラスに適用される場合は、<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute.SupportsProfiles%2A>プロパティに設定されている`true`の<xref:Microsoft.VisualStudio.Shell.ProvideOptionPageAttribute>クラスに適用されています。  
  
-   オートメーションをサポートします。  
  
 実装するオブジェクトの最小要件、**ツール オプション**ページを使用して<xref:Microsoft.VisualStudio.Shell.DialogPage>パブリック プロパティを追加します。  
  
 としてクラスが正しく登録されている場合、**ツール オプション**そのパブリック プロパティが 利用可能なプロバイダーのページ、**オプション**のセクションで、**ツール**のフォームのメニューで、プロパティ グリッドです。  
  
 これらすべての既定の機能をオーバーライドすることができます。 たとえばより高度なユーザーを作成するインターフェイスが必要のみの既定の実装をオーバーライドする<xref:Microsoft.VisualStudio.Shell.DialogPage.Window%2A>です。  
  
## <a name="example"></a>例  
 オプション ページの単純な"hello world"実装は、次に示します。 既定のプロジェクトに次のコードを追加すると、Visual Studio パッケージ テンプレートによって作成された、**メニュー コマンド**オプションを選択したオプション ページの機能をデモンストレーション適切にします。  
  
### <a name="description"></a>説明  
 次のクラスでは、最小限の"hello world"オプション ページを定義します。 ユーザーがパブリックに設定できます開かれると、`HelloWorld`プロパティ グリッド内のプロパティです。  
  
### <a name="code"></a>コード  
 [!code-csharp[UI_UserSettings_ToolsOptionPages #11](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_1.cs) ] [!code-vb [UI_UserSettings_ToolsOptionPages #11](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_1.vb)]  
  
### <a name="description"></a>説明  
 パッケージ クラスに次の属性を適用する ページのオプション使用できるように、パッケージを読み込むときにします。 数値は、カテゴリと、ページの任意のリソース Id と、最後にブール値では、ページがオートメーションをサポートしているかどうかを指定します。  
  
### <a name="code"></a>コード  
 [!code-csharp[UI_UserSettings_ToolsOptionPages #07](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_2.cs) ] [!code-vb [UI_UserSettings_ToolsOptionPages #07](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_2.vb)]  
  
### <a name="description"></a>説明  
 次のイベント ハンドラーには、[オプション] ページで設定されたプロパティの値に応じて結果が表示されます。 使用して、<xref:Microsoft.VisualStudio.Shell.Package.GetDialogPage%2A>ページによって公開されるプロパティにアクセスする、カスタム オプション ページの種類に結果を持つメソッドを明示的にキャストします。  
  
 パッケージ テンプレートによって生成されたプロジェクトの場合に、この関数からを呼び出す、`MenuItemCallback`に既定のコマンドにアタッチする機能が追加された、**ツール**メニュー。  
  
### <a name="code"></a>コード  
 [!code-csharp[UI_UserSettings_ToolsOptionPages #08](../../extensibility/internals/codesnippet/CSharp/creating-options-pages_3.cs) ] [!code-vb [UI_UserSettings_ToolsOptionPages #08](../../extensibility/internals/codesnippet/VisualBasic/creating-options-pages_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [拡張ユーザー設定とオプション](../../extensibility/extending-user-settings-and-options.md)   
 [オプション ページのオートメーションのサポート](../../extensibility/internals/automation-support-for-options-pages.md)
