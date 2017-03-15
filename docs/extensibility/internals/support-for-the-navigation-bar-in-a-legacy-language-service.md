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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 88636468da333fd9200f8661d88af6e7fdeedc59
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>従来の言語サービス内のナビゲーション バーのサポート
エディターのビューの上部にあるナビゲーション バーには、ファイル内の型とメンバーが表示されます。 種類は左ドロップダウンで表示され、メンバーを表示する右のボックスの一覧です。 ユーザーは、型を選択するキャレットは、型の最初の行に配置されます。 ユーザーは、メンバーを選択するときに、メンバーの定義のキャレットが配置されます。 ドロップ ダウン ボックスは、カーソルの現在の場所を反映するように更新されます。  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>表示およびナビゲーション バーを更新します。  
 ナビゲーション バーをサポートするためには派生クラスを<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>クラスし、実装、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッド</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A></xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>。 言語サービスがコード ウィンドウで、ベースに指定されている場合<xref:Microsoft.VisualStudio.Package.LanguageService>クラスをインスタンス化、<xref:Microsoft.VisualStudio.Package.CodeWindowManager>を含む、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>コード ウィンドウを表すオブジェクト</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow></xref:Microsoft.VisualStudio.Package.CodeWindowManager></xref:Microsoft.VisualStudio.Package.LanguageService>。 <xref:Microsoft.VisualStudio.Package.CodeWindowManager>オブジェクトが、新しいきます<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクト</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView></xref:Microsoft.VisualStudio.Package.CodeWindowManager>。 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>メソッドを取得、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクト</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars></xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>。 インスタンスを返す場合、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>クラス、<xref:Microsoft.VisualStudio.Package.CodeWindowManager>呼び出し、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>一覧表示し、内部に挿入する方法、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクトを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ドロップダウン バーのマネージャー</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 。 ドロップダウン リスト マネージャーで、バー、さらに、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>メソッドを<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>確立するためにオブジェクト、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>2 つのドロップダウン バーを保持するオブジェクト</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar></xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars></xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>。  
  
 キャレットを移動すると、<xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>メソッド</xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A></xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>。 基本の<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>メソッド<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>ナビゲーション バーの状態を更新するクラス</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>でメソッド</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>を呼び出す</xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> セットを渡す<xref:Microsoft.VisualStudio.Package.DropDownMember>このメソッドへのオブジェクト</xref:Microsoft.VisualStudio.Package.DropDownMember>。 各オブジェクトは、ドロップダウン リスト内のエントリを表します。  
  
## <a name="the-contents-of-the-navigation-bar"></a>ナビゲーション バーの内容  
 ナビゲーション バーの種類の一覧とメンバーの一覧が通常含まれています。 種類の一覧には、現在のソース ファイル内の利用可能なすべての型が含まれています。 型名には、完全な名前空間情報が含まれます。 2 種類が c# コードの例を次に示します。  
  
```c#  
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
  
 メンバーの一覧には、型の一覧で選択されている型の使用可能なメンバーが表示されます。 場合に、上記のコード例を使用して`TestLanguagePackage.TestLanguageService`が選択されている型は、メンバーの一覧には、プライベート メンバーが含まれます`tokens`と`serviceName`です。 内部構造`Token`は表示されません。  
  
 メンバー リスト内のキャレットを配置した場合は、メンバーの名前を太字を実装することができます。 メンバーできますにも表示されるグレー表示のテキストが、現在のキャレット位置のスコープ内でないを示します。  
  
## <a name="enabling-support-for-the-navigation-bar"></a>ナビゲーション バーのサポートの有効化  
 ナビゲーション バーのサポートを有効にするには、`ShowDropdownBarOption`のパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性を`true`</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>。 このパラメーターを設定、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>プロパティ</xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>。 ナビゲーション バーをサポートするためには、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars><xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A><xref:Microsoft.VisualStudio.Package.LanguageService>クラス</xref:Microsoft.VisualStudio.Package.LanguageService>のメソッド</xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>内のオブジェクト</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>を実装する必要があります。  
  
 実装で、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>メソッド場合、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>にプロパティが設定されている`true`、返すことができます、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクト</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars></xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A></xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>。 オブジェクトが返されない場合は、ナビゲーション バーは表示されません。  
  
 このコントロール エディターのビューが開いているときにリセットすることは、ユーザーがナビゲーション バーを表示するオプションを設定できます。 ユーザーは、閉じてから、変更が行われる前に、エディター ウィンドウを再び開く必要があります。  
  
## <a name="implementing-support-for-the-navigation-bar"></a>ナビゲーション バーのサポートを実装します。  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドは、2 つのリスト (各ボックスに&1; つ) と各リストの現在の選択項目を表す&2; つの値を受け取ります</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>。 リストと選択範囲の値を更新できる場合、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドが返す必要があります`true`リストが変更されていることを示すために</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>。  
  
 ドロップダウンの種類の選択範囲の変化に応じて、新しい種類を反映するように、メンバー リストを更新しなければなりません。 メンバー リストに表示内容は、いずれかができます。  
  
-   現在の型のメンバーの一覧。  
  
-   ソースで利用可能なすべてのメンバーは、ファイルしますが、灰色のテキストで表示される現在の型ではなく、すべてのメンバーを含む。 すばやく移動できますが、色は、現在選択されている型の一部ではないことを示しているように、ユーザーは灰色のメンバーを選択もできます。  
  
 実装、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドは、通常、次の手順を実行します</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>。  
  
1.  ソース ファイルの現在の宣言の一覧を取得します。  
  
     さまざまなリストを作成する方法があります。 カスタム メソッドのバージョンを作成する方法が、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスを呼び出す、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッド宣言のすべてのリストを返すカスタム解析理由を使用します</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A></xref:Microsoft.VisualStudio.Package.LanguageService>。 呼び出す別の方法があります、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドから直接、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>カスタム解析理由を持つメソッドです</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A></xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>。 キャッシュ内の宣言にする&3; つ目の方法が、<xref:Microsoft.VisualStudio.Package.AuthoringScope>の最後の完全解析操作から返されるクラス、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスを取り出してから、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッド</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A></xref:Microsoft.VisualStudio.Package.LanguageService></xref:Microsoft.VisualStudio.Package.AuthoringScope>。  
  
2.  設定またはの種類の一覧を更新します。  
  
     型リストの内容は、ソースが変更されたときに、または現在のキャレット位置に基づいて、種類のテキストのスタイルを変更する場合に更新することがあります。 この位置はなお、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッド</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>。  
  
3.  型リストに現在のキャレット位置に基づいて選択する種類を決定します。  
  
     現在のキャレット位置を囲む型を検索する、手順 1 で取得した宣言を検索し、型のリストにそのインデックスを特定するには、その型の種類の一覧を検索できます。  
  
4.  入力または選択した種類に基づくメンバーの一覧を更新します。  
  
     メンバー リストを反映に現在表示されて、**メンバー**ボックスの一覧です。 メンバーの一覧の内容は、ソースが変更された場合、または、選択した型のメンバーだけを表示して、選択した型が変更された場合に更新する必要があります。 ソース ファイル内のすべてのメンバーの表示を選択する場合は、一覧内の各メンバーのテキスト スタイルの設定を現在選択されている型が変更された場合に更新する必要があります。  
  
5.  現在のキャレット位置に基づいてメンバーの一覧から選択するメンバーを決定します。  
  
     現在のキャレット位置を含むメンバーを手順 1. で取得した宣言を検索し、メンバー リストにそのインデックスを特定するには、そのメンバーのメンバーの一覧を検索します。  
  
6.  返す`true`リストまたはいずれかの一覧の選択項目に変更が加えられた場合。
