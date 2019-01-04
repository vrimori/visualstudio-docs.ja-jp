---
title: プロパティ ウィンドウのボタン |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3229f95f81fe839b0dd84cd7d1294600c21bbc0e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934006"
---
# <a name="properties-window-buttons"></a>プロパティ ウィンドウのボタン
開発言語、製品の種類に応じて、既定では、ツールバーの特定のボタンが表示されます、**プロパティ**ウィンドウ。 すべてのケースで、 **Categorized**、 **Alphabetized**、**プロパティ**、および**プロパティ ページ**ボタンが表示されます。 Visual c# および Visual Basic の場合、**イベント**ボタンも表示されます。 特定の Visual C プロジェクトで、 **VC + + メッセージ**と**VC オーバーライド**ボタンが表示されます。 その他のプロジェクトの種類の他のボタンが表示されます。 ボタンの詳細については、**プロパティ**ウィンドウを参照してください[プロパティ ウィンドウ](../../ide/reference/properties-window.md)します。  
  
## <a name="implementation-of-properties-window-buttons"></a>プロパティ ウィンドウのボタンの実装  
 クリックすると、 **Categorized**ボタン、Visual Studio の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>をカテゴリにそのプロパティを並べ替えるにはフォーカスのあるオブジェクトのインターフェイス。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> 実装されている、`IDispatch`に提示されるオブジェクト、**プロパティ**ウィンドウ。  
  
 これには、負の値を持つ 11 の定義済みプロパティ カテゴリがあります。 カスタムのカテゴリを定義できますを割り当てることに、定義済みのカテゴリと区別するための正の値をお勧めします。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A>メソッドは、指定したプロパティの適切なプロパティのカテゴリ値を返します。 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A>メソッド カテゴリ名を含む文字列を返します。 のみ、Visual Studio は、標準的なプロパティのカテゴリの値を知っているために、カスタム カテゴリ値のサポートを提供する必要があります。  
  
 クリックすると、 **Alphabetized**ボタン名でアルファベット順にプロパティが表示されます。 名前によって取得`IDispatch`ローカライズされた並べ替えアルゴリズムに従ってします。  
  
 ときに、**プロパティ**ウィンドウが開いて、**プロパティ**自動的に表示されているボタンとして選択されています。 環境の他の部分で同じボタンが表示され、表示をクリックすることができます、**プロパティ**ウィンドウ。  
  
 **プロパティ ページ**ボタンが使用できない場合`ISpecifyPropertyPages`選択したオブジェクトが実装されていません。 プロパティ ページのソリューションやプロジェクトに通常関連付けられている表示構成に依存するプロパティがすることもできます (たとえば、Visual C) でプロジェクト項目に関連付けられます。  
  
> [!NOTE]
>  ツール バー ボタンを追加することはできません、**プロパティ**アンマネージ コードを使用してウィンドウ。 ツール バー ボタンを追加するから派生したマネージ オブジェクトを作成する必要があります<xref:System.Windows.Forms.Design.PropertyTab>します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティの拡張](../../extensibility/internals/extending-properties.md)