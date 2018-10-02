---
title: プロパティ ウィンドウのボタン |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 579f0a287e171872fccebbd251fae618ba615692
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544594"
---
# <a name="properties-window-buttons"></a>プロパティ ウィンドウのボタン
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[プロパティ ウィンドウのボタン](https://docs.microsoft.com/visualstudio/extensibility/internals/properties-window-buttons)します。  
  
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

