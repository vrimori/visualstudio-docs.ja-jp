---
title: "[ツールボックス アイテムの選択]、[WPF コンポーネント] | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
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
translationtype: Human Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 8d34a09ec4716a9ab2d5fbaea6c93657961c1c43
ms.lasthandoff: 02/22/2017

---
# <a name="choose-toolbox-items-wpf-components"></a>[ツールボックス アイテムの選択]、[WPF コンポーネント]
**[ツールボックス アイテムの選択]** ダイアログ ボックスのこのタブには、ローカル コンピューターで利用可能な Windows Presentation Foundation (WPF) コントロールの一覧が表示されます。 この一覧を表示するには、**[ツール]** メニューの **[ツールボックス アイテムの選択]** を選んで **[ツールボックス アイテムの選択]** ダイアログ ボックスを表示し、次に **[WPF コンポーネント]** タブを選びます。 コンポーネントの一覧を並べ替えるには、列ヘッダーをクリックします。  
  
-   コンポーネントの横にあるチェック ボックスをオンにすると、そのコンポーネントのアイコンが **[ツールボックス]** に表示されます。  
  
    > [!TIP]
    >  編集用に開かれるプロジェクト ドキュメントに WPF コントロールのインスタンスを追加するには、その**ツールボックス** アイコンをデザイン ビュー サーフェイスにドラッグします。 コンポーネントの既定のマークアップとコードがプロジェクトに挿入されて、変更できるようになります。 詳しくは、「[方法: ツールボックス ウィンドウの管理](http://msdn.microsoft.com/en-us/a022c3fe-298c-4a59-a48f-b050da90ebc2)」および「[[ツールボックス] タブの操作方法](http://msdn.microsoft.com/en-us/21285050-cadd-455a-b1f5-a2289a89c4db)」をご覧ください。  
  
-   コンポーネントの横にあるチェック ボックスをオフにすると、対応するアイコンが **[ツールボックス]** に表示されなくなります。  
  
    > [!NOTE]
    >  コンピューターにインストールされている .NET Framework コンポーネントは、アイコンが **[ツールボックス]** に表示されているかどうかに関係なく使用できます。  
  
 **[WPF コンポーネント]** タブの列には次の情報が含まれます。  
  
 名前  
 コンピューターのレジストリにエントリが存在する WPF コントロールの名前が一覧表示されます。  
  
 Namespace  
 コンポーネントの構造を定義している [NIB: .NET Framework クラス ライブラリ](http://msdn.microsoft.com/en-us/6c4f3a62-6a0f-41f2-9d52-ee0b13686f29)名前空間の階層構造が表示されます。 コンピューターにインストールされている各 .NET Framework 名前空間内で使用可能なコンポーネントを一覧表示するには、この列で並べ替えます。  
  
 アセンブリ名  
 各コンポーネントの名前空間を含む .NET Framework アセンブリの名前が表示されます。 コンピューターにインストールされている各 .NET Framework アセンブリに含まれる名前空間を一覧表示するには、この列で並べ替えます。  
  
 ディレクトリ  
 .NET Framework アセンブリの場所が表示されます。 アセンブリはすべて、既定では、グローバル アセンブリ キャッシュにあります。 グローバル アセンブリ キャッシュについて詳しくは、「[アセンブリとグローバル アセンブリ キャッシュの使用](http://msdn.microsoft.com/Library/8a18e5c2-d41d-49ef-abcb-7c27e2469433)」をご覧ください。  
  
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
 ツールボックスへのカスタム コントロールまたは <xref:System.Windows.Controls.UserControl> の追加には、以下の制限事項があります。  
  
-   現在のプロジェクトの外部で定義されたカスタム コントロールに対してのみ機能します。  
  
-   ソリューションの構成をデバッグからリリース、またはリリースからデバッグに変更したときに、正しく更新されません。 これは、参照がプロジェクト参照ではなく、ディスク上のアセンブリに対するものであるためです。 コントロールが現在のソリューションの一部である場合、デバッグからリリースに変更しても、プロジェクトは引き続きコントロールのデバッグ バージョンを参照します。  
  
 さらに、デザイン時のメタデータがカスタム コントロールに適用されていて、<xref:Microsoft.Windows.Design.ToolboxBrowsableAttribute> が `false` に設定されていることがこのメタデータで指定されている場合、コントロールはツールボックスに表示されません。  
  
 コントロールの名前空間とアセンブリをマッピングすることにより、XAML ビューでコントロールを直接参照できます。 詳しくは、「[方法 : 名前空間を XAML にインポートする](http://msdn.microsoft.com/en-us/6cda7c7a-369c-47dd-9c2d-13a35dcf737c)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [[ツールボックス アイテムの選択] ダイアログ ボックス (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [ツールボックス](../../ide/reference/toolbox.md)   
 [方法 : WPF アプリケーション内でサードパーティの WPF コントロールを使用する](http://msdn.microsoft.com/en-us/f4c0b601-3818-4f9f-85e5-77905f3b427f)   
 [WPF デザイナー](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)
