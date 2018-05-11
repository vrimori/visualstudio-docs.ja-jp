---
title: '方法: ASPX マークアップのローカライズ |Microsoft ドキュメント'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9dd127fea21a53b9a29082f536ac8c0404299c63
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-localize-aspx-markup"></a>方法: ASPX マークアップをローカライズする
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] (.aspx) ページは、通常の文字列をハードコード値を使用します。 これらの文字列をローカライズするには、ローカライズされたリソースを参照する式にそれらを置き換えます。  
  
## <a name="localizing-aspx-markup"></a>ASPX マークアップのローカライズ  
  
#### <a name="to-localize-aspx-markup"></a>ASPX マークアップをローカライズするには  
  
1.  別のリソース ファイルを追加します。 既定の言語と各ローカライズ言語。  
  
     マークアップおよびコードではなくだけをローカライズする場合は、グローバル リソース ファイル プロジェクト項目を追加します。 コードとマークアップをローカライズする場合は、リソース ファイル プロジェクト項目を追加します。  
  
    1.  グローバル リソース ファイルを追加する**ソリューション エクスプ ローラー**、SharePoint プロジェクト項目のショートカット メニューを開きを選択し、**追加**、**新しい項目の**します。 SharePoint で**2010**  ノードを選択して、**グローバル リソース ファイル**テンプレート。  
  
    2.  リソース ファイルを追加する**ソリューション エクスプ ローラー**、SharePoint プロジェクト項目のショートカット メニューを開きを選択し、**追加**、**新しい項目の**します。 いずれかで、 **Visual Basic**または**Visual c#**  ノードを選択して、**リソース ファイル**テンプレート。  
  
    > [!NOTE]  
    >  展開の種類プロパティを有効にする SharePoint プロジェクト項目にリソース ファイルを追加することを確認します。 このプロパティは、後で必要になります。 ソリューションが SharePoint プロジェクト項目を持たない場合は、空の SharePoint プロジェクトを追加し、その既定の Elements.xml ファイルを削除することができます。  
  
2.  既定の言語のリソース ファイルには、.resx 拡張子が付いた任意の名前を付けます (MyAppResources.resx など)。 ローカライズされたリソース ファイルごとに、同じ基本名の使用がカルチャを追加[!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]です。 (ドイツ語の場合は MyAppResources.de-DE.resx など)。  
  
3.  値を変更、**展開の種類**するには、各リソース ファイルのプロパティ**AppGlobalResource**させると、サーバーの App_GlobalResources フォルダーに配置します。  
  
4.  ASPX マークアップに加えてコードをローカライズするリソースを使用している場合は、値を受け入れ、**ビルド アクション**として各ファイルのプロパティ**埋め込まれたリソース**です。 マークアップのローカライズにのみ、リソース ファイルを使用する場合は、ファイルのプロパティの値を必要に応じて変更できます**コンテンツ**です。 詳細については、次を参照してください。 [SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)です。  
  
5.  各リソース ファイルを開き、各ファイルに同じ文字列 Id を使用する、ローカライズされた文字列を追加します。  
  
6.  [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ASPX ページまたはコントロールのマークアップをハードコーディングされた文字列値を置き換えて、次の形式を使用します。  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     たとえば、アプリケーション ページ上のラベル コントロールのテキストをローカライズするには、次のように変更。  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>  
    </asp:Content>  
    ```  
  
     から  
  
    ```  
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">  
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>  
    </asp:Content>  
    ```  
  
7.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
8.  SharePoint で、表示言語を既定の言語から変更します。  
  
     ローカライズされた文字列がアプリケーションに表示されます。 ローカライズされたリソースを表示するには、リソース ファイルのカルチャに対応する Language Pack が SharePoint サーバーにインストールされている必要があります。  
  
## <a name="see-also"></a>関連項目  
 [SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)   
 [方法: フィーチャーをローカライズ](../sharepoint/how-to-localize-a-feature.md)   
 [方法: リソース ファイルを追加](../sharepoint/how-to-add-a-resource-file.md)   
 [方法: コードをローカライズする](../sharepoint/how-to-localize-code.md)  
  
  