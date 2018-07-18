---
title: プロパティ ウィンドウのボタン |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 361333fdfceda28ecd78dc54145fded716ee81eb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130704"
---
# <a name="properties-window-buttons"></a>プロパティ ウィンドウのボタン
開発言語、製品の種類に応じて特定のボタンがツールバーに既定で表示される、**プロパティ**ウィンドウです。 すべての場合、 **Categorized**、 **Alphabetized**、**プロパティ**、および**プロパティ ページ**ボタンが表示されます。 Visual c# および Visual Basic で、**イベント**ボタンも表示されます。 特定の Visual C プロジェクトで、 **vc++ メッセージ**と**VC オーバーライド**ボタンが表示されます。 その他のプロジェクトの種類の他のボタンが表示されます。 ボタンの詳細については、**プロパティ**ウィンドウを参照してください[プロパティ ウィンドウ](../../ide/reference/properties-window.md)します。  
  
## <a name="implementation-of-properties-window-buttons"></a>プロパティ ウィンドウのボタンの実装  
 クリックすると、 **Categorized**  ボタン、Visual Studio の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>カテゴリでそのプロパティを並べ替えるにフォーカスがあるオブジェクトのインターフェイスです。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 実装される、`IDispatch`に提供されるオブジェクト、**プロパティ**ウィンドウです。  
  
 これには、負の値である必要が 11 の定義済みプロパティ カテゴリがあります。 カスタムのカテゴリを定義できますを割り当てることに正の値が定義済みのカテゴリと区別することをお勧めします。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>メソッドは、指定したプロパティの適切なプロパティ カテゴリ値を返します。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>メソッドをカテゴリ名を含む文字列を返します。 のみ、Visual Studio には、標準的なプロパティのカテゴリの値が認識しているために、カスタム カテゴリ値のサポートを提供する必要があります。  
  
 クリックすると、 **Alphabetized**ボタン、プロパティは名前でアルファベット順に表示されます。 名前が取得`IDispatch`ローカライズされた並べ替えアルゴリズムに従ってします。  
  
 ときに、**プロパティ** ウィンドウが開いて、**プロパティ**ボタンが自動的に表示される選択された状態でします。 環境の他の部分で同じボタンが表示されをクリックして表示することができます、**プロパティ**ウィンドウです。  
  
 **プロパティ ページ**ボタンが使用できない場合`ISpecifyPropertyPages`選択したオブジェクトが実装されていません。 プロパティ ページを通常ソリューションやプロジェクトに関連付けられている表示の構成に依存するプロパティでもかまいませんするも (たとえば、Visual C) でプロジェクト項目に関連付けられます。  
  
> [!NOTE]
>  ツール バー ボタンを追加することはできません、**プロパティ**ウィンドウでは、アンマネージ コードを使用します。 ツール バー ボタンを追加するから派生するマネージ オブジェクトを作成する必要があります<xref:System.Windows.Forms.Design.PropertyTab>です。  
  
## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)