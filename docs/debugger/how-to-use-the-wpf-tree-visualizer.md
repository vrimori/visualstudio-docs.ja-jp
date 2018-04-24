---
title: '方法: WPF ツリー ビジュアライザーを使用して |Microsoft ドキュメント'
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
ms.openlocfilehash: 290231b7b700a26945227ba04ddc2e97cdfe4299
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>方法: WPF ツリー ビジュアライザーを使用する
WPF ツリー ビジュアライザーを使用すると、WPF オプションのビジュアル ツリーを調べたり、ツリーに含まれるオブジェクトの WPF 依存関係プロパティを表示したりすることができます。 ビジュアル ツリーの詳細については、次を参照してください。 [wpf ツリー](/dotnet/framework/wpf/advanced/trees-in-wpf)です。 依存関係プロパティの詳細については、次を参照してください。[依存関係プロパティの概要](/dotnet/framework/wpf/advanced/dependency-properties-overview)です。  
  
 WPF ツリー ビジュアライザーを開くときに、2 つのペインが表示されます。**ビジュアル ツリー**左側、**のプロパティ***名前***:***型*ペイン右側です。 内のオブジェクトを選択して、**ビジュアル ツリー**  ウィンドウで、および**のプロパティ***名前***:***型*ウィンドウが自動的に更新が表示、そのオブジェクトのプロパティです。  
  
### <a name="to-open-the-wpf-tree-visualizer"></a>WPF ツリー ビジュアライザーを開くには  
  
1.  データヒントで、**ウォッチ**ウィンドウ、 **[自動変数]**ウィンドウ、または**[ローカル]** WPF オブジェクトの名前の横のウィンドウは、虫眼鏡アイコンの横にある矢印をクリックします。  
  
     ビジュアライザーの一覧が表示されます。  
  
2.  をクリックして**WPF ツリー ビジュアライザー**です。  
  
### <a name="to-search-the-visual-tree"></a>ビジュアル ツリーを検索するには  
  
-   **ビジュアル ツリー**ウィンドウ内で検索する文字列を入力、**検索**ボックス。  
  
     WPF ツリー ビジュアライザーで、入力した文字列と一致するビジュアル ツリー内の最初のオブジェクトが即時に検索されます。 より正確に一致する項目を検索するには、次の文字を入力します。  
  
    -   ビジュアル ツリー内の次の一致項目に移動するクリックして**次**です。  
  
    -   前の一致に戻って、をクリックして**Prev**です。  
  
    -   検索条件をクリアする をクリックして**オフ**です。  
  
### <a name="to-search-the-properties-list"></a>プロパティ リストを検索するには  
  
-   **プロパティの***名前***:***型* ウィンドウで、内で検索する文字列を入力、**フィルター**ボックス。  
  
     WPF ツリー ビジュアライザーで、入力した文字列と一致するプロパティが即時に検索され、入力した文字列と一致したこれらのプロパティのみが一覧に表示されます。 より正確に一致する項目を検索するには、次の文字を入力します。  
  
    -   検索条件をクリアする をクリックして**オフ**です。  
  
### <a name="to-close-the-visualizer"></a>ビジュアライザーを閉じるには  
  
-   クリックして、**閉じる** ダイアログ ボックスの右上隅のアイコン。  
  
## <a name="see-also"></a>関連項目  
 [カスタム ビジュアライザーを作成します。](../debugger/create-custom-visualizers-of-data.md)   
 [WPF のツリー](/dotnet/framework/wpf/advanced/trees-in-wpf)   
 [依存関係プロパティの概要](/dotnet/framework/wpf/advanced/dependency-properties-overview)