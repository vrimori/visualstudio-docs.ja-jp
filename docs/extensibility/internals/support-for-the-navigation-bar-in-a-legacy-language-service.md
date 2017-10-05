---
title: "従来の言語サービス内のナビゲーション バーのサポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 16
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
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: eb5212c4828ad24256447bc1c75f85ec0d9d9579
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>従来の言語サービス内のナビゲーション バーのサポート
エディター ビューの上部にあるナビゲーション バーは、ファイル内の型とメンバーを表示します。 型は左側ドロップダウンに表示され、メンバーを表示する右のドロップダウンします。 ユーザーは、型を選択する型の最初の行にカーソルが配置されます。 ユーザーは、メンバーを選択するときにカーソルが、メンバーの定義に配置されます。 ドロップ ダウン ボックスは、そのキャレットの現在の場所を反映するように更新されます。  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>表示およびナビゲーション バーを更新します。  
 サポートするには、ナビゲーション バーからクラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>クラスし、実装、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドです。 言語サービスはコード ウィンドウで、ベースを付与するときに<xref:Microsoft.VisualStudio.Package.LanguageService>クラスをインスタンス化、<xref:Microsoft.VisualStudio.Package.CodeWindowManager>が含まれている、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>コード ウィンドウを表すオブジェクト。 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 、新しいオブジェクトが割り当てられて、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクト。 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>メソッドを取得、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクト。 インスタンスを返す場合、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>クラス、<xref:Microsoft.VisualStudio.Package.CodeWindowManager>呼び出し、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>を一覧表示し、内部に挿入する方法、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクトを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ドロップダウン バー マネージャー。 ドロップダウン リスト マネージャーで、バー、さらに、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>メソッドを<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>確立するためにオブジェクト、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> 2 つのドロップダウン バーを保持するオブジェクト。  
  
 カレットを移動すると、<xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>メソッドです。 基本<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>ナビゲーション バーの状態を更新するクラス。 セットを渡す<xref:Microsoft.VisualStudio.Package.DropDownMember>このメソッドにオブジェクト。 各オブジェクトは、ドロップダウン リストのエントリを表します。  
  
## <a name="the-contents-of-the-navigation-bar"></a>ナビゲーション バーの内容  
 ナビゲーション バーの種類の一覧とメンバーの一覧が通常含まれています。 種類の一覧には、現在のソース ファイルで使用可能なすべての型が含まれています。 型名には、完全な名前空間情報が含まれます。 2 種類の c# コードの例を次に示します。  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 型の一覧が表示されます`TestLanguagePackage.TestLanguageService`と`TestLanguagePackage.TestLanguageService.Tokens`です。  
  
 メンバーの一覧には、型の一覧で選択されている型の使用可能なメンバーが表示されます。 場合は、上記のコード例を使用して`TestLanguagePackage.TestLanguageService`が選択されている型メンバーの一覧には、プライベート メンバーにが含まれます`tokens`と`serviceName`です。 内部構造`Token`は表示されません。  
  
 カレットがその内部にある場合は、メンバーの名前を太字にメンバーの一覧を実装することができます。 メンバーできますにも表示されるテキスト、淡色表示であること、現在のカレット位置のスコープを示すです。  
  
## <a name="enabling-support-for-the-navigation-bar"></a>ナビゲーション バーのサポートを有効にします。  
 ナビゲーション バーのサポートを有効にするを設定する必要があります、`ShowDropdownBarOption`のパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性を`true`です。 このパラメーターは、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> プロパティを設定します。 ナビゲーション バーをサポートするために実装する必要があります、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>内のオブジェクト、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>メソッドを<xref:Microsoft.VisualStudio.Package.LanguageService>クラスです。  
  
 実装で、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>メソッド場合、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>プロパティに設定されている`true`、返すことができます、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクト。 オブジェクトが返されない場合、ナビゲーション バーは表示されません。  
  
 このコントロール エディター ビューが開いている状態にリセットすることは、ユーザーがナビゲーション バーを表示するオプションを設定できます。 ユーザーは、閉じるされ、変更が行われる前に、エディター ウィンドウを閉じて再度開きます必要があります。  
  
## <a name="implementing-support-for-the-navigation-bar"></a>ナビゲーション バーのサポートを実装します。  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドは、2 つのリスト (1 つは各ドロップダウン) および各リストの現在の選択を表す 2 つの値を取得します。 リストと選択の値を更新できる場合、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドが返す必要があります`true`リストが変更されたことを示すためにします。  
  
 選択範囲が変わると種類のドロップダウンで、新しい型を反映するように、メンバーの一覧を更新しなければなりません。 メンバーの一覧に表示される内容と、いずれかのことができます。  
  
-   現在の型のメンバーの一覧です。  
  
-   ソースで利用可能なすべてのメンバーは、ファイルしますが、現在の型ではなく、すべてのメンバーに灰色のテキストで表示。 ユーザーが灰色のメンバーを選択できるは、すばやく移動できるように、使用できるため、色は、現在選択されている型の一部であるいないことを示しますもします。  
  
 実装、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドは、通常、次の手順を実行します。  
  
1.  ソース ファイルの現在の宣言の一覧を取得します。  
  
     リストを追加する方法の数があります。 1 つの方法は、のバージョンでカスタム メソッドを作成する、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスを呼び出す、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>すべての宣言の一覧を返すカスタム解析理由を持つメソッドです。 呼び出す別の方法があります、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドから直接、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>カスタム解析理由を持つメソッドです。 宣言をキャッシュする 3 番目のアプローチがあります、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 、フル解析の最後の操作によって返されるクラス、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスし、をから取得、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドです。  
  
2.  設定または種類の一覧を更新します。  
  
     型一覧の内容は、現在のキャレット位置に基づいて、種類のテキストのスタイルを変更するを選択した場合や、ソースが変更されたときに更新することがあります。 この位置に渡されることに注意してください、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドです。  
  
3.  型リストに現在のキャレット位置に基づいて選択する種類を決定します。  
  
     現在のカレット位置を囲む型を検索する、手順 1 で取得された宣言を検索しの型リストにそのインデックスを特定するには、その型の種類の一覧を検索できます。  
  
4.  入力または選択した種類に基づくメンバーの一覧を更新します。  
  
     メンバーの一覧の反映に現在表示されて、**メンバー**ドロップダウンします。 メンバーの一覧の内容は、ソースが変更された場合、または選択した種類のメンバーのみを表示して、選択した型が変更された場合に更新する必要があります。 ソース ファイル内のすべてのメンバーを表示する場合は、一覧内の各メンバーのテキストのスタイルを現在選択されている型が変更された場合に更新する必要があります。  
  
5.  現在のキャレット位置に基づいてメンバーの一覧から選択するメンバーを決定します。  
  
     現在のカレット位置を含むメンバーを手順 1. で取得された宣言を検索し、メンバーの一覧にそのインデックスを特定するには、そのメンバーのメンバーの一覧を検索します。  
  
6.  返す`true`をリストまたはいずれかの一覧で選択内容が変更された場合。
