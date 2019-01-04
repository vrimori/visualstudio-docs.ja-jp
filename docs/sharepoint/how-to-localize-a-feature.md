---
title: '方法: フィーチャーをローカライズ |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 165eee357c001720af132236a8577f259efa4f24
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887679"
---
# <a name="how-to-localize-a-feature"></a>方法: フィーチャーをローカライズします。
  機能のタイトルと説明は、既定では、ハード コーディングされた文字列値を使用します。 フィーチャーのタイトルと説明をローカライズするには、ローカライズされたリソースを参照する式で、文字列を置き換えます。  
  
## <a name="localize-a-feature"></a>フィーチャーをローカライズします。  
  
#### <a name="to-localize-a-feature"></a>フィーチャーをローカライズするには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **Feature1**ノードを選び、**フィーチャー リソースの追加**します。  
  
2.  **リソースの追加** ダイアログ ボックスで、選択**インバリアント言語**既定の言語機能のリソース ファイルのカルチャとして一覧からします。  
  
3.  ローカライズ機能用に任意の言語リソース ファイルを選択しながら、ローカライズされた言語ごとに、前の手順を繰り返します。  
  
     別のフィーチャー リソース ファイルが作成されます。 既定の言語と各ローカライズをサポートする言語。  
  
4.  リソース エディターで、各リソース ファイルを開くし、すべての文字列 Id とその値を入力します。  
  
     たとえば、既定のフィーチャー リソース ファイル内の文字列 ID を入力**タイトル**の値を持つ**フィーチャーのタイトルを My**、2 つ目の文字列の ID と**説明**の値を持つ**機能説明**します。 各ローカライズされたリソース ファイルの Id の既定の機能のリソースで使用されるのと同じ文字列を使用して、ローカライズされた文字列値を入力します。  
  
5.  すべてのリソースの値を入力した後は、機能のショートカット メニューを開き (たとえば、 *Feature1.feature*)、選び、**ビュー デザイナー**フィーチャー デザイナーでこの機能を開くにします。  
  
6.  ローカライズする、**タイトル**と**説明**機能では、フィールドでは、次の形式を使用して、そのボックスに値を入力します。  
  
     `$Resources:` *文字列 ID*  
  
     たとえば、$resources:string を入力します:**タイトル**で、**フィーチャーのタイトル**ボックス、および $resources:string:**説明**で、**機能の説明**ボックス.  
  
     文字列 Id は、リソース ファイルで使用されているものと一致する必要があります。  
  
7.  選択、 **F5**キー、アプリケーションをビルドして実行します。  
  
8.  SharePoint では、開く、**サイトの操作** メニューの 選択**サイト設定**、、**サイトの操作**セクションを選択して、 **サイト機能の管理**リンク。  
  
9. SharePoint で、表示言語を既定の言語から変更します。  
  
     アプリケーションでは、機能のローカライズされたタイトルと説明が表示されます。 ローカライズされたリソースを表示するには、リソース ファイルのカルチャに対応する Language Pack が SharePoint サーバーにインストールされている必要があります。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションをローカライズします。](../sharepoint/localizing-sharepoint-solutions.md)   
 [方法: リソース ファイルを追加します。](../sharepoint/how-to-add-a-resource-file.md)   
 [方法: ASPX マークアップをローカライズします。](../sharepoint/how-to-localize-aspx-markup.md)   
 [方法: コードをローカライズします。](../sharepoint/how-to-localize-code.md)  
