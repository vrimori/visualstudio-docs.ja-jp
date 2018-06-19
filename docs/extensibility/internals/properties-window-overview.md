---
title: プロパティ ウィンドウの概要 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e255795a52064723477eda4e1aca532adedb6be1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131621"
---
# <a name="properties-window-overview"></a>プロパティ ウィンドウの概要
**プロパティ**で利用可能な期間の 2 種類の主要で選択したオブジェクトのプロパティを表示するウィンドウを使用、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。 これら 2 つの種類のウィンドウは次のとおりです。  
  
-   ソリューション エクスプ ローラー、クラス ビュー、およびオブジェクト ブラウザーなどのツール ウィンドウ  
  
-   このようなエディターや、フォーム デザイナー、XML エディター、および HTML エディターとデザイナーが含まれているドキュメント ウィンドウ  
  
## <a name="using-the-properties-window"></a>[プロパティ] ウィンドウを使用します。  
 **プロパティ**ウィンドウが 1 つまたは複数選択した項目のプロパティを表示します。 複数の項目が選択されている場合は、選択したすべてのオブジェクトのすべてのプロパティの交差部分が表示されます。  
  
 フォームのデザイン ウィンドウまたは COM + メタデータを使用して HTML エディター内で選択したオブジェクトに関連するイベントに表示されます、**プロパティ**ウィンドウです。 たとえば、ボタンを選択し、その関連するイベントを表示、`OnClick`イベントで、そのボタンにリンクできます。  
  
 表示されるイベント、**プロパティ**ウィンドウは、主に、コードにバインドされているオブジェクトを使用します。 コードを行うには何もないファイル形式を編集している場合、すべてのイベントがあるしません。 イベントにのみ表示されます、**プロパティ**コードや特定のオブジェクトに関連付けられている特定のイベントを実行している間のバインドがあるときにウィンドウです。 この例は、そのオブジェクトがアクティブになったときに実行される、選択したオブジェクトに隠れているコードになります。  
  
 次の表で使用するプライマリ インターフェイス、**プロパティ**ウィンドウです。  
  
|インターフェイス名|説明|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|カテゴリの一覧を示します、**プロパティ**ウィンドウの各プロパティをカテゴリにマップします。|  
|[IDispatch インターフェイス](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)|オブジェクトのメソッドとプロパティ プログラミング ツールと自動化をサポートする他のアプリケーションを公開します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|省略記号 (...) ボタンと呼ばれる*ビルダー*オブジェクト自体によって実装されたモーダル ダイアログ ウィンドウを開くことです。 値に簡単に型指定されていないテキスト フィールドでユーザーが場合、使用されます。 たとえばを開くには、カラー ピッカーの RGB 値を決定する使用可能性があります。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|表示される情報を更新するためのオブジェクトにアクセスできるように、**プロパティ**ウィンドウです。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 各ウィンドウを表示する関連のプロパティで選択可能オブジェクトを含む Vspackage によって実装されます。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|インターフェイスと、構造体のフィールドのメソッドなどのオブジェクトの種類に関する情報を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|選択項目のイベントの通知を受け取ると、現在のプロジェクト階層、項目、要素の値、およびコマンド UI コンテキストに関する情報を取得する Vspackage を有効にします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|複数の選択内容にアクセスできる環境を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|表示される一部のプロパティのローカライズされた名前を提供するために使用、**プロパティ**ウィンドウです。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|現在の選択、要素の値、またはコマンド UI コンテキストの変更の登録済みの Vspackage に通知します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|現在の選択が変更された環境に通知し、新しい選択に関連する階層と項目の情報へのアクセスを提供します。|  
  
 詳細については`IDispatch`、MSDN ライブラリを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [拡張プロパティ](../../extensibility/internals/extending-properties.md)   
 [プロパティ ウィンドウのフィールドとインターフェイス](../../extensibility/internals/properties-window-fields-and-interfaces.md)