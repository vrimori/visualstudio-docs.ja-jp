---
title: コントロールのバインド ダイアログ ボックスのカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.datasource.datauicustomization
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Customize Control Binding dialog box
ms.assetid: abcc0be3-a18e-4f47-b354-d6b0c618e087
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8ca2da23040f3e7a57fe5da2ff8b87cc7fc38099
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49889712"
---
# <a name="customize-control-binding-dialog-box"></a>[コントロールのバインドのカスタマイズ] ダイアログ ボックス
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

使用して、**コントロールのバインドのカスタマイズ**内の項目に使用できるコントロールを指定する ダイアログ ボックス、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)します。  
  
 内の各項目、**データソース**ウィンドウには、項目にバインドできるコントロールのリストが関連付けられます。 各項目に使用できるコントロールは、項目のデータ型によって決まります。 データの種類ごとには、このダイアログ ボックスで、既定のコントロールなどで定義されている、有効な関連付けられたコントロールの一覧があります。  
  
 データ バインド コントロールを作成するデザイン サーフェイスに項目をドラッグする前に作成するには、どのコントロールを選択できます。 項目をドラッグする場合、**データソース**ウィンドウを選択した項目のデータ型がデザイン サーフェイスに追加された場合に、コントロールの既定のコントロールを選択することがなく、デザイン画面にします。  
  
 このダイアログ ボックスを使用して、コントロール内の項目のリストをカスタマイズする方法について、**データ ソース**ウィンドウを参照してください[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。  
  
## <a name="uielement-list"></a>UIElement の一覧  
 **データ型**  
 コントロールに関連付ける型の一覧が表示されます。  
  
- テーブル、エンティティ、およびオブジェクトとして表される **[一覧]** 型。  
  
- 列またはエンティティとオブジェクトのパブリック プロパティは、基になるデータ ストア内のプロパティまたは列の実際のデータ型として表されます。  
  
- ユーザー定義の図形をオブジェクトとして表現されます **[その他]** します。 たとえば、アプリケーションにデータ オブジェクトの 1 つ以上のプロパティを表示するカスタム コントロールがある場合は、選択、 **[その他]** コントロールのデータ型。  
  
  **関連付けられているコントロール**  
  特定のデータ型に関連付けることができるコントロールの一覧が表示されます。 特定のコントロールで選択されているデータ型に関連付ける場合、**データ型**一覧で、対応するチェック ボックスをオンにします。 関連付けを削除する チェック ボックスをオフにします。 コントロールで表示されるショートカット メニューに表示のチェック、**データ ソース**関連付けられているデータ型の項目のウィンドウ。  
  
  一覧にコントロールを追加するにはいくつかのデータ バインディング属性の 1 つを持つコントロールを追加して、**ツールボックス**します。 詳細については、次を参照してください。[データ ソース ウィンドウにカスタム コントロールを追加](../data-tools/add-custom-controls-to-the-data-sources-window.md)します。  
  
  **既定を設定します。**  
  選択したコントロール型の既定の選択したデータ型の項目を割り当てます。 表示されるショートカット メニューの最初の選択項目として既定のコントロールが表示されます、**データソース**項目のウィンドウ。 1 つだけのコントロール型は、データ型の既定値として割り当てることができます。  
  
  **既定値のクリア**  
  選択したデータ型の既定値として、コントロールの指定を削除します。 選択したデータの種類の既定値がない場合は **[なし]** によって提示されるショートカット メニューの最初の選択項目として表示されます、**データ ソース**項目に関連付けの種類のウィンドウ。  
  
## <a name="see-also"></a>関連項目  
 [[データ ソース] ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [新しいデータ ソースを追加します。](../data-tools/add-new-data-sources.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [データ ソース ウィンドウにカスタム コントロールを追加します。](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [[データ ソース] ウィンドウからドラッグしたときに作成されるコントロールを設定する](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)