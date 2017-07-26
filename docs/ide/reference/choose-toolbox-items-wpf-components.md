---
title: "[ツールボックス アイテムの選択]、[WPF コンポーネント] | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.chooseitems.wpfcomponents
helpviewer_keywords:
- WPF Components tab, Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box, WPF Components tab
ms.assetid: 6ce1d178-88c0-4295-8915-59fdeedabb11
caps.latest.revision: 13
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d2f4eba36e9069a35cf279ccf1c78f72a51d77a1
ms.openlocfilehash: b574aef447309842b5ff02be72dae291407f0ddb
ms.contentlocale: ja-jp
ms.lasthandoff: 06/23/2017

---
# <a name="choose-toolbox-items-wpf-components"></a>[ツールボックス アイテムの選択]、[WPF コンポーネント]
**[ツールボックス アイテムの選択]** ダイアログ ボックスのこのタブには、ローカル コンピューターで利用可能な Windows Presentation Foundation (WPF) コントロールの一覧が表示されます。 この一覧を表示するには、**[ツール]** メニューの **[ツールボックス アイテムの選択]** を選んで **[ツールボックス アイテムの選択]** ダイアログ ボックスを表示し、次に **[WPF コンポーネント]** タブを選びます。 コンポーネントの一覧を並べ替えるには、列ヘッダーをクリックします。  

-   コンポーネントの横にあるチェック ボックスをオンにすると、そのコンポーネントのアイコンが **[ツールボックス]** に表示されます。  

    > [!TIP]
    >  編集用に開かれるプロジェクト ドキュメントに WPF コントロールのインスタンスを追加するには、その**ツールボックス** アイコンをデザイン ビュー サーフェイスにドラッグします。 コンポーネントの既定のマークアップとコードがプロジェクトに挿入されて、変更できるようになります。 詳細については、「[ツールボックスの使用](../../ide/using-the-toolbox.md)」を参照してください。  

-   コンポーネントの横にあるチェック ボックスをオフにすると、対応するアイコンが **[ツールボックス]** に表示されなくなります。  

    > [!NOTE]
    >  コンピューターにインストールされている .NET Framework コンポーネントは、アイコンが **[ツールボックス]** に表示されているかどうかに関係なく使用できます。  

 **[WPF コンポーネント]** タブの列には次の情報が含まれます。  

 名前  
 コンピューターのレジストリにエントリが存在する WPF コントロールの名前が一覧表示されます。  

 名前空間  
 コンポーネントの構造を定義している [.NET Framework クラス API](/dotnet/api/?view=netframework-4.7) 名前空間の階層構造が表示されます。 コンピューターにインストールされている各 .NET Framework 名前空間内で使用可能なコンポーネントを一覧表示するには、この列で並べ替えます。  

 アセンブリ名  
 各コンポーネントの名前空間を含む .NET Framework アセンブリの名前が表示されます。 コンピューターにインストールされている各 .NET Framework アセンブリに含まれる名前空間を一覧表示するには、この列で並べ替えます。  

 ディレクトリ  
 .NET Framework アセンブリの場所が表示されます。 アセンブリはすべて、既定では、グローバル アセンブリ キャッシュにあります。 グローバル アセンブリ キャッシュについて詳しくは、「[アセンブリとグローバル アセンブリ キャッシュの使用](/dotnet/framework/app-domains/working-with-assemblies-and-the-gac)」をご覧ください。  

## <a name="uielement-list"></a>UIElement の一覧  
 **フィルター**  
 テキスト ボックスに入力した文字列に基づいて、WPF コントロールの一覧をフィルター処理します。 4 つの列のいずれかで一致したものがすべて表示されます。  

 **クリア**  
 フィルター文字列をクリアします。  

 **参照**  
 **[開く]** ダイアログ ボックスが開き、WPF コントロールを含むアセンブリに移動することができます。 グローバル アセンブリ キャッシュに含まれないアセンブリを読み込むには、これを使います。  

 **Language**  
 選んだ WPF コントロールを含むアセンブリのローカライズされた言語を表示します。  

## <a name="limitations"></a>制限事項  
 ツールボックスにカスタム コントロールや <xref:System.Windows.Controls.UserControl> を追加するとき、次の制限があります。  

-   現在のプロジェクトの外部で定義されたカスタム コントロールに対してのみ機能します。  

-   ソリューションの構成をデバッグからリリース、またはリリースからデバッグに変更したときに、正しく更新されません。 これは、参照がプロジェクト参照ではなく、ディスク上のアセンブリに対するものであるためです。 コントロールが現在のソリューションの一部である場合、デバッグからリリースに変更しても、プロジェクトは引き続きコントロールのデバッグ バージョンを参照します。  

 さらに、デザイン時のメタデータがカスタム コントロールに適用されていて、<xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> が `false` に設定されていることがこのメタデータで指定されている場合、コントロールはツールボックスに表示されません。  

 コントロールの名前空間とアセンブリをマッピングすることにより、XAML ビューでコントロールを直接参照できます。  

## <a name="see-also"></a>関連項目  
 [ツールボックス](../../ide/reference/toolbox.md)

 [WPF の概要](../../designers/getting-started-with-wpf.md)

