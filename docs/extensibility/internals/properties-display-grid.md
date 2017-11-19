---
title: "プロパティ グリッドの表示 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35b36c357c9b98d81627eea0d511b0b4fd49f693
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="properties-display-grid"></a>プロパティ グリッドの表示
**プロパティ**ウィンドウには、グリッド内のフィールドが表示されます。 左の列には、プロパティの名前が含まれています。右側の列には、プロパティの値が含まれています。  
  
## <a name="working-with-the-grid"></a>グリッドの使用  
 2 つの列リストでは、デザイン時とその現在の設定の変更可能な構成に依存しないプロパティを示します。 すべてのプロパティを表示しない場合があることに注意してください。 プロパティを設定することができます、実装することで、たとえば、隠しファイルとして、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>メソッドです。 具体的には、子プロパティを持つプロパティを非表示にします。  
  
1.  設定、`pfDisplay`パラメーター<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A>に`FALSE`です。  
  
2.  設定、`pfHide`パラメーター<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>に`TRUE`です。  
  
 情報を送信する、**プロパティ**ウィンドウ、IDE を使用して<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>です。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>各ウィンドウに表示する関連のプロパティで選択可能オブジェクトを含む Vspackage によって呼び出されますが、**プロパティ**ウィンドウです。 **ソリューション エクスプ ローラー**の実装<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>呼び出し`GetProperty`を使用して<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層内の参照可能なオブジェクトを取得する、プロジェクト階層にします。  
  
 VSPackage がサポートされていない場合<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>、IDE を使用しようとしました。<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>の値を使用して<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層アイテムまたはアイテムを提供します。  
  
 VSPackage が作成する必要はありません、プロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>を実装する IDE が指定したウィンドウ パッケージのため (たとえば、**ソリューション エクスプ ローラー**) 構築<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>の代わりにします。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>IDE によって呼び出される 3 つの方法で構成されます。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>表示される選択されたオブジェクトの数を表す、**プロパティ**ウィンドウです。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>返します、`IDispatch`に表示される選択されているオブジェクト、**プロパティ**ウィンドウです。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>によって返されるオブジェクトのいずれにもできるようになります<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>ユーザーが選択します。 これにより、VSPackage を視覚的に、UI 内のユーザーに表示される選択を更新できます。  
  
 **プロパティ**ウィンドウからの情報を抽出し、`IDispatch`選ばれたプロパティを取得するオブジェクト。 プロパティ ブラウザーを使用して`IDispatch`オブジェクトにどのようなプロパティを確認することをサポートしているクエリを実行して`ITypeInfo`から取得される`IDispatch::GetTypeInfo`です。 ブラウザーの設定にこれらの値を使用して、**プロパティ**ウィンドウと個々 のプロパティの値がグリッドに表示を変更します。 プロパティの情報は、オブジェクト自体内で管理されます。  
  
 返されたオブジェクトをサポートしているため`IDispatch`、呼び出し元を呼び出して、オブジェクトの名前などの情報を取得できます`IDispatch::Invoke`または`ITypeInfo::Invoke`目的の情報を表す定義済みのディスパッチ識別子 (DISPID) をします。 宣言された Dispid は負の値をユーザー定義の識別子と競合しないことを確認します。  
  
 **プロパティ**ウィンドウには、異なる種類のフィールドによっては、選択したオブジェクトの特定のプロパティの属性が表示されます。 これらのフィールドには、エディット ボックス、ドロップダウン リスト、およびカスタム エディター ダイアログ ボックスへのリンクが含まれます。  
  
-   列挙された一覧に含まれている値は、<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>にクエリを実行`IDispatch`です。 フィールド名をダブルクリックするか、値をクリックし、ドロップダウン リストから新しい値を選択すると、プロパティ グリッドで列挙された一覧から取得された値を変更できます。 プロパティの列挙リストの設定は定義済みで、プロパティ リストにプロパティ名をダブルクリックすると、使用可能な選択肢を循環参照します。 True または false などの 2 つの選択肢で定義済みのプロパティの選択肢の間で切り替えるには、プロパティ名をダブルクリックします。  
  
-   場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>は`false`を示す、値が変更されたことは、値が太字で表示されます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>値を元の値にリセットすることができるかどうかの判断に使用されます。 そのため、値を右クリックして既定値に戻す変更できる場合**リセット**表示されるメニューからです。 それ以外の場合、既定値に戻す値を手動で変更する必要があります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>ローカライズし、デザイン時に表示されるプロパティの名前を非表示にすることもできますが、実行時に表示されるプロパティ名には影響しません。  
  
-   省略記号 (...) ボタンをクリックすると、(カラー ピッカーやフォントの一覧) 元となるユーザーが選択できるプロパティの値の一覧が表示されます。 <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>これらの値を提供します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)