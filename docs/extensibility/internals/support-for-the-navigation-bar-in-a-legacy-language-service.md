---
title: 従来の言語サービスでのナビゲーション バーのサポート |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9fc9d4339978f84b02a5c922c06139031924bf4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868814"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>従来の言語サービスでのナビゲーション バーのサポート
エディター ビューの上部にあるナビゲーション バーでは、ファイル内の型とメンバーを表示します。 種類は左ドロップダウンで表示され、メンバーを表示する右のドロップダウン リスト。 ユーザーは、型を選択する型の最初の行にキャレットが配置されます。 ユーザーがメンバーと、メンバーの定義にカーソルが配置されます。 ドロップダウン ボックスのキャレットの現在の場所を反映するように更新されます。  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>表示およびナビゲーション バーを更新します。  
 ナビゲーション バーをサポートするからクラスを派生する必要があります、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>クラスし、実装、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッド。 言語サービスはコード ウィンドウで、ベースを指定するときに<xref:Microsoft.VisualStudio.Package.LanguageService>クラスをインスタンス化、<xref:Microsoft.VisualStudio.Package.CodeWindowManager>が含まれています、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>コード ウィンドウを表すオブジェクト。 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 、新しいオブジェクトを指定します<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>オブジェクト。 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>メソッドの取得、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクト。 インスタンスを返す場合、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>クラス、<xref:Microsoft.VisualStudio.Package.CodeWindowManager>呼び出し、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>を一覧表示し、内部に挿入する方法、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクトを[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ドロップダウン バーのマネージャー。 ドロップダウン バー マネージャーで、さらに、呼び出し、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>メソッドを<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>確立するためにオブジェクト、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>ドロップダウン リストの 2 つのバーを保持するオブジェクト。  
  
 カレットを移動すると、<xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>メソッド。 基本<xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>メソッドの呼び出し、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドで、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>のナビゲーション バーの状態を更新するクラス。 セットを渡す<xref:Microsoft.VisualStudio.Package.DropDownMember>このメソッドにオブジェクト。 各オブジェクトは、ドロップダウン リスト内のエントリを表します。  
  
## <a name="the-contents-of-the-navigation-bar"></a>ナビゲーション バーの内容  
 ナビゲーション バーの種類の一覧とメンバーの一覧が通常含まれています。 種類の一覧には、現在のソース ファイル内のすべての種類が含まれています。 型名には、完全な名前空間情報が含まれます。 2 種類の c# コードの例を次に示します。  
  
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
  
 型の一覧が表示されます`TestLanguagePackage.TestLanguageService`と`TestLanguagePackage.TestLanguageService.Tokens`します。  
  
 メンバーの一覧には、型の一覧で選択されている型の使用可能なメンバーが表示されます。 場合に、上記のコード例を使用して`TestLanguagePackage.TestLanguageService`が選択されている型メンバーの一覧には、プライベート メンバーにが含まれます`tokens`と`serviceName`します。 内部構造`Token`は表示されません。  
  
 キャレットがその内部に配置した場合、メンバーの名前を太字にするメンバーの一覧を実装することができます。 メンバーも表示できますでグレー表示テキスト、キャレットが現在配置されているスコープ内でないことを示します。  
  
## <a name="enabling-support-for-the-navigation-bar"></a>ナビゲーション バーのサポートを有効にします。  
 ナビゲーション バーのサポートを有効に設定する必要があります、`ShowDropdownBarOption`のパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>属性を`true`します。 このパラメーターは、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> プロパティを設定します。 ナビゲーション バーをサポートするために実装する必要があります、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクト、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>メソッドを<xref:Microsoft.VisualStudio.Package.LanguageService>クラス。  
  
 実装で、<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>メソッド場合、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>プロパティに設定されて`true`、返すことができます、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>オブジェクト。 オブジェクトを返さない場合、ナビゲーション バーは表示されません。  
  
 エディターのビューが開いている状態にリセットするには、このコントロールできるように、ユーザーがナビゲーション バーを表示するオプションを設定できます。 ユーザーは、閉じるし、変更が行われる前に、エディター ウィンドウを再び開く必要があります。  
  
## <a name="implementing-support-for-the-navigation-bar"></a>ナビゲーション バーのサポートを実装します。  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドは 2 つのリスト (各ボックスに 1 つ) と各リストの現在の選択を表す 2 つの値を受け取ります。 リストと選択の値を更新できる場合、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドが返す必要があります`true`をリストが変更されたことを示します。  
  
 ドロップダウン リストの種類の選択が変更された、メンバーの一覧、新しい型を反映するように更新する必要があります。 メンバーの一覧に表示内容は、いずれかを指定できます。  
  
- 現在の型のメンバーの一覧。  
  
- ソースで使用可能なすべてのメンバーは、ファイルしますが、淡色のテキストに表示される現在の型ではなく、すべてのメンバーを含む。 ユーザーは、クイック ナビゲーションのために使用できますが、色は、現在選択されている型の一部ではないことを示します、灰色のメンバーを選択もできます。  
  
  実装、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッドは通常、次の手順を実行します。  
  
1.  ソース ファイルの現在の宣言の一覧を取得します。  
  
     リストを設定する方法を数多くあります。 1 つの方法は、のバージョンでカスタム メソッドを作成する、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスを呼び出す、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>カスタム解析理由は、すべての宣言の一覧を返すメソッド。 呼び出す別の方法があります、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドから直接、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>理由は、カスタムな parse メソッド。 3 番目のアプローチがキャッシュ内の宣言することがあります、<xref:Microsoft.VisualStudio.Package.AuthoringScope>クラスの最後の完全な解析操作によって返される、<xref:Microsoft.VisualStudio.Package.LanguageService>クラスを取得する、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッド。  
  
2.  設定または型の一覧を更新します。  
  
     種類の一覧の内容は、ソースが変更されたとき、または現在のカレット位置に基づく種類のテキストのスタイルを変更することを選択した場合に更新することがあります。 注この位置に渡される、<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>メソッド。  
  
3.  現在のカレット位置に基づく種類の一覧から選択する種類を決定します。  
  
     現在のカレット位置を囲む型を検索する、手順 1 で取得した宣言を検索し、型の一覧にそのインデックスを判断するには、その型の種類の一覧を検索できます。  
  
4.  入力または選択した型に基づくメンバーの一覧を更新します。  
  
     メンバー リストの反映に現在表示されて、**メンバー**ドロップダウンします。 メンバーの一覧の内容は、ソースが変更された場合、または、選択した型のメンバーだけを表示して、選択した型が変更された場合に更新する必要があります。 ソース ファイル内のすべてのメンバーを表示する場合は、一覧内の各メンバーのテキスト スタイルを現在選択されている型が変更された場合に更新する必要があります。  
  
5.  現在のカレット位置に基づいてメンバーの一覧から選択するメンバーを決定します。  
  
     現在のカレット位置を含むメンバーを手順 1. で取得した宣言を検索し、メンバーの一覧にそのインデックスを判断するには、そのメンバーのメンバーの一覧を検索します。  
  
6.  返す`true`リスト、またはいずれかの一覧の選択項目への変更を加えた場合。