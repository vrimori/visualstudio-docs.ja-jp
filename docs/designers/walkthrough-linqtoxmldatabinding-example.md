---
title: "チュートリアル: LinqToXmlDataBinding の例 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aedf42e8-896c-48fa-88df-7f7c9536aa69
caps.latest.revision: 2
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ec8e44f5299154b0781a16c43ba485c1be076467
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-linqtoxmldatabinding-example"></a>チュートリアル : LinqToXmlDataBinding の例
このチュートリアルでは、LinqToXmlDataBinding の例を示し、L2DBForm.xaml と L2DBForm.xaml.cs という&2; つの主要なソース ファイルに関する興味深い情報をいくつか説明します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルをお読みになる前に、「[方法 : LinqToXmlDataBinding という例をビルドして実行する](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)」の説明に従って、LinqToXmlDataBinding プログラムをビルドして実行することを強くお勧めします。  
  
## <a name="remarks"></a>コメント  
 LinqToXmlDataBinding プログラムは、C# ソース ファイルと XAML ソース ファイルで構成される Windows Presentation Foundation (WPF) アプリケーションです。 このプログラムには書籍の一覧を定義する組み込み XML ドキュメントが含まれており、ユーザーはそれらのエントリを表示、追加、削除、および編集することができます。 このプログラムは、次の&2; つの主要なソース ファイルで構成されています。  
  
-   L2DBForm.xaml には、メイン ウィンドウのユーザー インターフェイス (UI) の XAML 宣言コードが含まれています。 また、書籍一覧のデータ プロバイダーと組み込み XML ドキュメントを定義するウィンドウ リソース セクションも含まれています。  
  
-   L2DBForm.xaml.cs には、UI に関連付けられている初期化メソッドとイベント処理メソッドが含まれています。  
  
 メイン ウィンドウは縦に区切られ、次の&4; つの UI セクションに分かれています。  
  
-   **[XML]** には、組み込まれている書籍一覧の生の XML ソースが表示されます。  
  
-   **[Book List]** には書籍エントリが標準テキストで表示され、ユーザーはエントリを個別に選択および削除できます。  
  
-   **[Edit Selected Book]** では、ユーザーは現在選択している書籍エントリに関連付けられている値を編集できます。  
  
-   **[Add New Book]** では、ユーザーが入力した値に基づいて新しい書籍エントリを作成できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[L2DBForm.xaml ソース コード](../designers/l2dbform-xaml-source-code.md)|L2DBForm.xaml ファイルの XAML コードの内容と説明を示します。|  
|[L2DBForm.xaml.cs ソース コード](../designers/l2dbform-xaml-cs-source-code.md)|L2DBForm.xaml.cs ファイルの C# ソース コードの内容と説明を示します。|  
  
## <a name="see-also"></a>関連項目  
 [LINQ to XML を使用した WPF のデータ バインディングの例](../designers/wpf-data-binding-using-linq-to-xml-example.md)   
 [方法: LinqToXmlDataBinding という例をビルドして実行する](../designers/how-to-build-and-run-the-linqtoxmldatabinding-example.md)
