---
title: プロパティ グリッドの表示 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 52bda19b6b4acf02b70963ab52431334d2f1f1fc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49836672"
---
# <a name="properties-display-grid"></a>プロパティ表示グリッド
**プロパティ**ウィンドウには、グリッド内のフィールドが表示されます。 左側の列には、プロパティの名前が含まれています。右側の列には、プロパティ値が含まれています。  
  
## <a name="working-with-the-grid"></a>グリッドの使用  
 2 つの列の一覧は、デザイン時と、現在の設定は変更可能な構成に依存しないプロパティを示します。 すべてのプロパティが表示しないことに注意してください。 プロパティを設定すると非表示で、実装することなどによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>メソッド。 具体的には、子プロパティを持つプロパティを非表示にします。  
  
1. 設定、`pfDisplay`パラメーター<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A>に`FALSE`します。  
  
2. 設定、`pfHide`パラメーター<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>に`TRUE`します。  
  
   プッシュ情報を**プロパティ**ウィンドウで、IDE を使用して<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>します。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 各ウィンドウに表示される関連するプロパティで選択可能なオブジェクトを含む Vspackage によって呼び出される、**プロパティ**ウィンドウ。 **ソリューション エクスプ ローラー**の実装の<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>呼び出し`GetProperty`を使用して<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>で、プロジェクト階層にある階層内の参照可能なオブジェクトを取得します。  
  
   VSPackage がサポートされていない場合<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>、IDE を使用しようとしました。<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>の値を使用して<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>階層アイテムまたはアイテムを指定します。  
  
   VSPackage が作成する必要はありません、プロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>を実装するウィンドウを IDE が指定したパッケージがあるため (たとえば、**ソリューション エクスプ ローラー**) を構築します<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>の代わりに。  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> IDE によって呼び出される 3 つの方法で構成されます。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> 表示される選択されたオブジェクトの数が含まれています、**プロパティ**ウィンドウ。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> 返します、`IDispatch`に表示される選択されているオブジェクト、**プロパティ**ウィンドウ。  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> によって返されるオブジェクトのいずれかの可能<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>ユーザーによって選択されます。 これにより、UI 内のユーザーに表示される選択項目を視覚的に更新するには、VSPackage ができます。  
  
  **プロパティ**ウィンドウからの情報を抽出して、`IDispatch`参照されているプロパティを取得するオブジェクト。 プロパティ ブラウザーを使用して`IDispatch`オブジェクトにどのようなプロパティを要求するクエリを実行して、サポートしています。 `ITypeInfo`、がから取得される`IDispatch::GetTypeInfo`します。 ブラウザーの設定にこれらの値で使用し、**プロパティ**ウィンドウと変更がグリッド内の個々 のプロパティの値が表示されます。 プロパティの情報は、オブジェクト自体内で維持されます。  
  
  返されたオブジェクトをサポートしているため`IDispatch`、呼び出し元は、いずれかを呼び出すことによって、オブジェクトの名前などの情報を取得できます`IDispatch::Invoke`または`ITypeInfo::Invoke`で必要な情報を表す定義済みのディスパッチ識別子 (DISPID)。 宣言された Dispid は負の値をユーザー定義の識別子と競合しないことを確認します。  
  
  **プロパティ**ウィンドウには、さまざまな種類の選択したオブジェクトの特定のプロパティの属性に応じてフィールドが表示されます。 これらのフィールドには、エディット ボックス、ドロップダウン リスト、およびカスタム エディター ダイアログ ボックスへのリンクが含まれます。  
  
- によって列挙された一覧に含まれる値を取得、<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>クエリ`IDispatch`します。 フィールド名をダブルクリックするか、値をクリックし、ドロップダウン リストから新しい値を選択して、プロパティ グリッドで列挙された一覧から取得した値を変更できます。 列挙された一覧から設定定義済みのプロパティ のプロパティ の一覧でプロパティ名をダブルクリックは、使用できる選択肢を循環します。 定義済みのプロパティを true または false などの 2 つだけ選択の選択項目間を切り替えるプロパティ名をダブルクリックします。  
  
- 場合<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>は`false`、こと、値が変更された、値が太字で表示されます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> 値を元の値にリセットすることができるかどうかの判断に使用されます。 そのため、値を右クリックして、既定値に変更できる場合**リセット**表示されるメニューから。 それ以外の場合、既定値で、値を手動で変更があります。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ローカライズし、デザイン時に表示されるプロパティの名前を非表示にすることもできますが、実行時に表示されるプロパティ名には影響しません。  
  
- 省略記号 (...) ボタンをクリックすると、(カラー ピッカーやフォントの一覧) 元のユーザーが選択できるプロパティの値の一覧が表示されます。 <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> これらの値を提供します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)