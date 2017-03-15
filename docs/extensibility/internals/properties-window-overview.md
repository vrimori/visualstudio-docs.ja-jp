---
title: "プロパティ ウィンドウの概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 11
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
ms.openlocfilehash: 1ec1a650c72fbd181d176aea84b228c9973ad526
ms.lasthandoff: 02/22/2017

---
# <a name="properties-window-overview"></a>プロパティ ウィンドウの概要
**プロパティ**で利用可能な期間の&2; 種類の主要で選択したオブジェクトのプロパティを表示 ウィンドウが使用される、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。 これら&2; つの種類のウィンドウは次のとおりです。  
  
-   ソリューション エクスプ ローラー、クラス ビュー、およびオブジェクト ブラウザーなどのツール ウィンドウ  
  
-   このようなエディターや、フォーム デザイナー、XML エディターでは、HTML エディターとデザイナーが含まれているドキュメント ウィンドウ  
  
## <a name="using-the-properties-window"></a>[プロパティ] ウィンドウを使用します。  
 **プロパティ**ウィンドウには、1 つまたは複数選択した項目のプロパティが表示されます。 複数の項目を選択すると、選択したすべてのオブジェクトのすべてのプロパティの交差部分が表示されます。  
  
 フォームのデザイン ウィンドウまたは COM + メタデータを使用して HTML エディター内で選択したオブジェクトに関連するイベントが表示される、**プロパティ**ウィンドウです。 たとえば、ボタンを選択しなどの関連するイベントを表示、`OnClick`イベントで、そのボタンにリンクできます。  
  
 表示されるイベント、**プロパティ**ウィンドウは、主にコードにバインドされているオブジェクトを使用します。 コードとはまったく関係がないファイル形式を編集している場合、すべてのイベントがあるしません。 イベントでのみ表示、**プロパティ**コードと特定のオブジェクトに関連付けられている特定のイベントを実行している間のバインディングがある場合は、ウィンドウです。 この例は、そのオブジェクトがアクティブ化されるときに実行される、選択したオブジェクトの分離コードになります。  
  
 次の表は、プライマリで使用するインターフェイス、**プロパティ**ウィンドウです。  
  
|インターフェイス名|説明|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties></xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|カテゴリの一覧を提供、**プロパティ**ウィンドウし、各プロパティをカテゴリにマップします。|  
|[IDispatch インターフェイス](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|オブジェクトのメソッドおよびプログラミング ツールおよび自動化をサポートするその他のアプリケーションのプロパティを公開します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder></xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|省略記号 (...) ボタンと呼ばれる*ビルダー*オブジェクト自体によって実装されたモーダル ダイアログ ウィンドウを開くことです。 値がテキスト フィールド内のユーザーが簡単に型指定しない場合に使用されます。 たとえばを開くにはカラー ピッカーの RGB 値を決定する使用可能性があります。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer></xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|表示される情報の更新に使用されるオブジェクトにアクセスできるように、**プロパティ**ウィンドウです。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>各ウィンドウを表示する関連のプロパティで選択可能オブジェクトを含む Vspackage によって実装されます。</xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo></xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|インターフェイスと構造体のフィールドのメソッドなどのオブジェクトの種類について説明します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection></xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Vspackages にある選択項目のイベントの通知を受け取ると、現在のプロジェクト階層、項目、要素の値、およびコマンド UI のコンテキストに関する情報を取得を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect></xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|複数の項目にアクセスできる環境を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing></xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|表示される一部のプロパティのローカライズされた名前を指定するために使用、**プロパティ**ウィンドウです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|現在の選択、要素の値、またはコマンド UI コンテキストに対する変更の登録済みの VSPackages に通知します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx></xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|現在の選択項目が変更された環境に通知し、新しい選択範囲に関連する階層と項目の情報へのアクセスを提供します。|  
  
 詳細については`IDispatch`、MSDN ライブラリを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [プロパティを拡張します。](../../extensibility/internals/extending-properties.md)   
 [プロパティ ウィンドウのフィールドとインターフェイス](../../extensibility/internals/properties-window-fields-and-interfaces.md)
