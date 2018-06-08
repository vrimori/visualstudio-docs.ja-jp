---
title: XAML のエラーと警告
ms.date: 03/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a263f361e28c515f1694238c4d60fdeffb95f03a
ms.sourcegitcommit: 58052c29fc61c9a1ca55a64a63a7fdcde34668a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34746625"
---
# <a name="xaml-errors-and-warnings"></a>XAML のエラーと警告

Visual Studio では、XAML を作成するとき、入力したコードがすぐに解析されます。 エラーが検出されると、コード行に波線が付きます。 この波線にマウス カーソルを合わせると、エラーまたは警告に関する詳細が表示されます。 一部のエラーと警告にはクイック アクションの電球が表示されます。**Ctrl**+**.** キーボード ショートカットで 問題解決のための選択肢が表示されます。

## <a name="error-types"></a>エラーの種類

バックグラウンドでは、複数のツールにより並列で XAML が解析されます。 XAML エラーは、エラーを検出したツールに基づき、次の 3 つの種類の 1 つに分類されます。

|**エラーを検出した機能**|**エラー コードの形式**|
|--------------------------------|-----------------|
|XAML 言語サービス (XAML エディター)|XLSxxxx|
|XAML デザイナー|XDGxxxx|
|XAML エディット コンティニュ|XECxxxx|

> [!Note]
> 一部のエラー/警告には該当コードがありません。 そのようなエラーは通常、XAML デザイナーが検出したエラーです。


## <a name="suppress-xaml-designer-errors"></a>XAML デザイナー エラー

**[ツール]、[オプション]** の順に選択して **[オプション]** ダイアログを開き、**[テキスト エディター]、[XAML]、[その他]** の順に選択します。

**[Show errors detected by the XAML designer]\(XAML デザイナーによって検出されたエラーを表示する\)** チェック ボックスの選択を解除します。

![XAML デザイナー エラー](../designers/media/suppress_xaml_designer_errors.png)


