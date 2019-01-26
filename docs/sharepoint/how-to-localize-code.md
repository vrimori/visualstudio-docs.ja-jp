---
title: '方法: コードのローカライズ |Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8d61f9f0dff98d25185233fcf07bc937de3a6455
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862800"
---
# <a name="how-to-localize-code"></a>方法: コードをローカライズします。
  ローカライズされていないコードでは、ハードコーディングされた文字列値が使用されています。 コードの文字列をローカライズするには、それらを <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> の呼び出しに置き換えます。このメソッドは、ローカライズされたリソースを参照します。  
  
## <a name="localize-code"></a>コードをローカライズします。  
  
#### <a name="to-localize-code"></a>コードをローカライズするには  
  
1.  **ソリューション エクスプ ローラー**プロジェクトの項目でショートカット メニューを開き、選択し、**追加** > **モジュール**します。  
  
     選択、**リソース ファイル**テンプレート。  
  
    > [!NOTE]  
    >  Deployment Type プロパティを使用できるように、SharePoint プロジェクト項目にリソース ファイルを必ず追加します。 このプロパティは、後で必要になります。  
  
2.  既定の言語リソース ファイルの名前が付いた任意の *.resx*拡張子など*MyAppResources.resx*します。  
  
3.  ローカライズ言語ごとに手順 1. と 2. を繰り返して、SharePoint プロジェクト項目にそれぞれのリソース ファイルを追加します。  
  
     ローカライズされた各リソース ファイルに対しては、同じ基本名にカルチャ ID を加えた名前を使用します  たとえば、リソースのローカライズ、ドイツ語の名前*MyAppResources.de」という*します。  
  
4.  各リソース ファイルを開いて、ローカライズされた文字列を追加します。 各ファイルで同じ文字列 ID を使用します。  
  
5.  値を変更、**展開の種類**プロパティには、各リソース ファイルの**AppGlobalResource**各ファイルが、サーバーの App_GlobalResources フォルダーに配置します。  
  
6.  値を受け入れ、**ビルド アクション**プロパティとして各ファイルの**埋め込まれたリソース**します。  
  
     埋め込みリソースはプロジェクトの DLL にコンパイルされます。  
  
7.  プロジェクトをビルドして、リソースのサテライト DLL を作成します。  
  
8.  **パッケージ デザイナー**、選択、 **[詳細設定]** タブをクリックし、サテライト アセンブリを追加します。  
  
9. **場所**ボックスにカルチャ ID のフォルダーを場所のパスを先頭に追加など、 *DE-DE\\\<プロジェクト項目の名前 >. resources.dll*します。  
  
10. ソリューションで System.Web アセンブリがまだ参照されていない場合は System.Web アセンブリへの参照を追加し、<xref:System.Web> に対するディレクティブをコードに追加します。  
  
11. UI テキスト、エラー、メッセージ テキストなど、ユーザーへの表示用にコード内でハードコーディングされている文字列をすべて見つけます。 それらの文字列を、次の構文を使用する <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> メソッドの呼び出しに置き換えます。  
  
    ```csharp  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. 選択、 **F5**キー、アプリケーションをビルドして実行します。  
  
13. SharePoint で、表示言語を既定の言語から変更します。  
  
     ローカライズされた文字列がアプリケーションに表示されます。 ローカライズされたリソースを表示するには、リソース ファイルのカルチャに対応する Language Pack が SharePoint サーバーにインストールされている必要があります。  
  
## <a name="see-also"></a>関連項目
 [SharePoint ソリューションをローカライズします。](../sharepoint/localizing-sharepoint-solutions.md)   
 [方法: フィーチャーをローカライズします。](../sharepoint/how-to-localize-a-feature.md)   
 [方法: ASPX マークアップをローカライズします。](../sharepoint/how-to-localize-aspx-markup.md)   
 [方法: リソース ファイルを追加します。](../sharepoint/how-to-add-a-resource-file.md)  
