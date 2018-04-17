---
title: XAML のエラーと警告 | Microsoft Docs
ms.date: 03/06/2018
ms.technology: vs-ide-designers
ms.topic: article
ms.assetid: 34eac8a0-7ec5-4c40-b97a-0126ed367931
author: karann-msft
ms.author: karann
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60e29417e1a993adfb2c4bb7c78a6f1ed0209cef
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/03/2018
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

![XAML デザイナー エラーを非表示にする](../designers/media/suppress_xaml_designer_errors.PNG "SuppressXAMLDesignerErrors")


