---
title: "方法: フィーチャーをローカライズ |Microsoft ドキュメント"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 03adaa74feacc82c5f63c1930f7dad63cc931433
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-localize-a-feature"></a>方法: フィーチャーをローカライズする
  フィーチャーのタイトルと説明は、既定では、ハード コーディングされた文字列値を使用します。 フィーチャーのタイトルと説明をローカライズするには、ローカライズされたリソースを参照する式で、文字列を置き換えます。  
  
## <a name="localizing-a-feature"></a>フィーチャーのローカライズ  
  
#### <a name="to-localize-a-feature"></a>フィーチャーをローカライズするには  
  
1.  **ソリューション エクスプ ローラー**、ショートカット メニューを開き、 **Feature1**  ノードを選択し**フィーチャー リソースの追加**です。  
  
2.  **リソースの追加** ダイアログ ボックスで、選択**インバリアント言語**既定の言語機能のリソース ファイルのカルチャに応じて、リストからです。  
  
3.  ローカライズされたフィーチャーの任意の言語のリソース ファイルを選択しながら、ローカライズされた言語ごとに、前の手順を繰り返します。  
  
     別のフィーチャー リソース ファイルが作成されます。 既定の言語と各ローカライズをサポートする言語。  
  
4.  リソース エディターで、各リソース ファイルを開くし、すべての文字列 Id とその値を入力します。  
  
     たとえば、既定のフィーチャー リソース ファイル内の文字列 ID を入力**タイトル**の値を持つ**マイ フィーチャーのタイトル**、2 つ目の文字列 ID と**説明**の値を持つ**機能説明**です。 各ローカライズされたリソース ファイル、文字列と同じ既定のフィーチャー リソースで使用される Id を使用しますが、ローカライズされた文字列値を入力します。  
  
5.  機能 (たとえば、Feature1.feature) のショートカット メニューを開き、すべてのリソースの値を入力すると後、順に選択**ビュー デザイナー**を開くには、フィーチャー デザイナーで機能します。  
  
6.  ローカライズする、**タイトル**と**説明**機能では、フィールドでは、次の形式を使用して、そのボックスに値を入力します。  
  
     `$Resources:`*文字列 ID*  
  
     たとえば、$Resources を入力:**タイトル**で、**フィーチャーのタイトル**ボックス、および $Resources:**説明**で、**機能の説明**ボックス.  
  
     文字列 Id は、リソース ファイルで使用されていると一致する必要があります。  
  
7.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
8.  SharePoint では、開く、**サイトの操作** メニューの 選択**サイト設定**、、**サイトの操作**セクションを選択、 **サイト機能の管理**リンクします。  
  
9. SharePoint で、表示言語を既定の言語から変更します。  
  
     アプリケーションでは、ローカライズされたフィーチャーのタイトルと説明が表示されます。 ローカライズされたリソースを表示するには、リソース ファイルのカルチャに対応する Language Pack が SharePoint サーバーにインストールされている必要があります。  
  
## <a name="see-also"></a>参照  
 [SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)   
 [方法: リソース ファイルを追加](../sharepoint/how-to-add-a-resource-file.md)   
 [方法: ASPX マークアップのローカライズ](../sharepoint/how-to-localize-aspx-markup.md)   
 [方法: コードをローカライズする](../sharepoint/how-to-localize-code.md)  
  
  