---
title: プロパティ ウィンドウの概要 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38579bcfee3aa390d9135006b8fc57f7b4b06b0f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993304"
---
# <a name="properties-window-overview"></a>プロパティ ウィンドウの概要
**プロパティ**で利用可能な期間の 2 つの主な型で選択したオブジェクトのプロパティを表示するウィンドウが使用される、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。 これら 2 つの種類のウィンドウは次のとおりです。  
  
-   ソリューション エクスプ ローラー、クラス ビュー、およびオブジェクト ブラウザーなどのツール ウィンドウ  
  
-   このようなエディターや、フォーム デザイナー、XML エディター、HTML エディターとデザイナーを格納しているドキュメント ウィンドウ  
  
## <a name="using-the-properties-window"></a>[プロパティ] ウィンドウを使用します。  
 **プロパティ**ウィンドウが 1 つまたは複数選択した項目のプロパティを表示します。 複数の項目を選択すると、選択したすべてのオブジェクトのすべてのプロパティの積集合が表示されます。  
  
 フォームのデザイン ウィンドウまたは COM + のメタデータを使用して HTML エディター内で選択したオブジェクトに関連するイベントに表示されます、**プロパティ**ウィンドウ。 たとえば、ボタンを選択し、関連するイベントを表示、`OnClick`イベントで、そのボタンにリンクできます。  
  
 表示されるイベント、**プロパティ**ウィンドウは、主に、コードにバインドされているオブジェクトを使用します。 コードとは何もしていないファイル形式を編集している場合、すべてのイベントがあるしません。 イベントにのみ表示されます、**プロパティ**ウィンドウ コードや特定のオブジェクトに関連付けられている特定のイベントを実行している間のバインドがある場合。 この例は、そのオブジェクトがアクティブ化されるときに実行される、選択したオブジェクトの後ろのコードになります。  
  
 次の表に、によって使用されるプライマリ インターフェイス、**プロパティ**ウィンドウ。  
  
|インターフェイス名|説明|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|カテゴリの一覧を示します、**プロパティ**ウィンドウの各プロパティをカテゴリにマップされます。|  
|[IDispatch インターフェイス](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|オブジェクトのメソッドとプロパティ プログラミング ツールとオートメーションをサポートする他のアプリケーションを公開します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|省略記号 (...) ボタンが呼び出されます*ビルダー*オブジェクト自体によって実装されたモーダル ダイアログ ウィンドウを開くです。 値を簡単に型指定されていないテキスト フィールド内のユーザーによって場合、使用されます。 たとえばの RGB 値を決定するカラー ピッカーを開きます使用可能性があります。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|表示される情報の更新に使用されるオブジェクトにアクセスできるように、**プロパティ**ウィンドウ。 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> 各ウィンドウを表示する関連のプロパティで選択可能オブジェクトを含む Vspackage によって実装されます。|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|インターフェイスと構造体のフィールドのメソッドなどのオブジェクトの種類について説明します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Vspackage の選択項目のイベント通知を受け取ると、現在のプロジェクト階層、項目、要素の値、およびコマンド UI コンテキストに関する情報を取得できるようにします。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|複数の選択内容にアクセスできる環境を提供します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|表示される一部のプロパティのローカライズされた名前を指定するために使用、**プロパティ**ウィンドウ。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|現在の選択、要素の値、またはコマンド UI コンテキストへの変更の登録済みの Vspackage に通知します。|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|現在選択されている変更を環境に通知し、新しい選択範囲に関連する階層と項目の情報へのアクセスを提供します。|  
  
 詳細については`IDispatch`、MSDN ライブラリを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)   
 [プロパティ ウィンドウのフィールドとインターフェイス](../../extensibility/internals/properties-window-fields-and-interfaces.md)