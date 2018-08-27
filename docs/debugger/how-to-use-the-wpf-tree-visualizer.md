---
title: '方法: WPF ツリー ビジュアライザーを使用する |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0a478eae1e576ba2556d48f6527f6c9e2dab4ef6
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "42902164"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>方法: WPF ツリー ビジュアライザーを使用する
WPF ツリー ビジュアライザーを使用すると、WPF オプションのビジュアル ツリーを調べたり、ツリーに含まれるオブジェクトの WPF 依存関係プロパティを表示したりすることができます。 ビジュアル ツリーの詳細については、次を参照してください。 [WPF のツリー](/dotnet/framework/wpf/advanced/trees-in-wpf)します。 依存関係プロパティの詳細については、次を参照してください。[依存関係プロパティの概要](/dotnet/framework/wpf/advanced/dependency-properties-overview)します。  
  
 WPF ツリー ビジュアライザーを開くと、2 つのペインが表示されます。**ビジュアル ツリー**左側、**プロパティの**_名前_**:** _型_右側のウィンドウ。 内のオブジェクトを選択、**ビジュアル ツリー**ウィンドウで、および**のプロパティ**_名前_**:**_型_ペインがそのオブジェクトのプロパティを表示する自動的に更新されます。  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>WPF ツリー ビジュアライザーを開くには  
  
1.  データヒントで、**ウォッチ**ウィンドウ、 **[自動変数]** ウィンドウ、または**ローカル**ウィンドウで、WPF オブジェクト名の横にある虫眼鏡アイコンの横の矢印をクリックします。  
  
     ビジュアライザーの一覧が表示されます。  
  
2.  クリックして**WPF ツリー ビジュアライザー**します。  
  
### <a name="to-search-the-visual-tree"></a>ビジュアル ツリーを検索するには  
  
-   **ビジュアル ツリー**ウィンドウ内で検索する文字列を入力、**検索**ボックス。  
  
     WPF ツリー ビジュアライザーで、入力した文字列と一致するビジュアル ツリー内の最初のオブジェクトが即時に検索されます。 より正確に一致する項目を検索するには、次の文字を入力します。  
  
    -   ビジュアル ツリー内の次の一致に移動して、次のようにクリックします。**次**します。  
  
    -   前の一致に戻って、次のようにクリックします。 **Prev**します。  
  
    -   検索条件をクリアする をクリックして**オフ**します。  
  
### <a name="to-search-the-properties-list"></a>プロパティ リストを検索するには  
  
-   **プロパティの**_名前_**:**_型_ウィンドウ内で検索する文字列を入力、 **をフィルター処理**ボックス。  
  
     WPF ツリー ビジュアライザーで、入力した文字列と一致するプロパティが即時に検索され、入力した文字列と一致したこれらのプロパティのみが一覧に表示されます。 より正確に一致する項目を検索するには、次の文字を入力します。  
  
    -   検索条件をクリアする をクリックして**オフ**します。  
  
### <a name="to-close-the-visualizer"></a>ビジュアライザーを閉じるには  
  
-   をクリックして、**閉じる** ダイアログ ボックスの右上隅のアイコン。  
  
## <a name="see-also"></a>関連項目  
 [カスタム ビジュアライザーを作成します。](../debugger/create-custom-visualizers-of-data.md)   
 [WPF のツリー](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [依存関係プロパティの概要](/dotnet/framework/wpf/advanced/dependency-properties-overview)
