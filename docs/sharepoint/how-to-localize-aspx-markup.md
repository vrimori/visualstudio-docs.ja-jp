---
title: "方法: ASPX マークアップをローカライズする | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ローカライズ (XML を) [Visual Studio での SharePoint 開発]"
  - "Visual Studio での SharePoint 開発, ローカライズ"
ms.assetid: 9559a1d1-6558-4c24-a51e-c6ee79432778
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# 方法: ASPX マークアップをローカライズする
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] \(.aspx\) ページでは、通常、ハードコーディングされた文字列値が使用されています。  それらの文字列をローカライズするには、ローカライズされたリソースを参照する式に置き換えます。  
  
## ASPX マークアップのローカライズ  
  
#### ASPX マークアップをローカライズするには  
  
1.  既定の言語用と各ローカライズ言語用の個別のリソース ファイルを追加します。  
  
     ローカライズするのはマークアップだけで、コードはローカライズしない場合は、グローバル リソース ファイル プロジェクト項目を追加します。  コードとマークアップをローカライズする場合は、リソース ファイル プロジェクト項目を追加します。  
  
    1.  追加するには、グローバル リソースは、**\[ソリューション エクスプローラー\]** で開き、SharePoint のプロジェクト項目のショートカット メニューをクリックし、**\[追加\]** をクリックします、**\[新しいアイテム\]** を格納します。  SharePoint **2010** ノードで、**\[グローバル リソース ファイル\]** テンプレートを選択します。  
  
    2.  リソース ファイルを、**\[ソリューション エクスプローラー\]** に追加するには、SharePoint プロジェクト項目のショートカット メニューを開き、**\[新しいアイテム\]**、**\[追加\]** をクリックします。  **\[Visual Basic\]** または **\[Visual C\#\]** ノードで、**\[アセンブリ リソース ファイル\]** テンプレートを選択します。  
  
    > [!NOTE]  
    >  \[配置タイプ\] プロパティを使用できるように、SharePoint プロジェクト項目にリソース ファイルを必ず追加します。  このプロパティは、後で必要になります。  ソリューションに SharePoint プロジェクト項目がない場合は、空の SharePoint プロジェクトを追加し、既定の Elements.xml ファイルを削除できます。  
  
2.  既定の言語のリソース ファイルには、.resx 拡張子が付いた任意の名前を付けます \(MyAppResources.resx など\)。  同じ基本名を各ローカライズ リソース ファイルで使用します。ただし、カルチャ [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)]を追加します。  \(ドイツ語の場合は MyAppResources.de\-DE.resx など\)。  
  
3.  、サーバーの App\_GlobalResources フォルダーに配置されるように **\[AppGlobalResource\]** に各リソース ファイルの **\[配置タイプ\]** のプロパティの値を変更します。  
  
4.  ASPX マークアップだけでなくコードのローカライズしたらにリソースを使用する場合 **\[埋め込みリソース\]** として各ファイルの **\[ビルド アクション\]** のプロパティの値をそのまま使用します。  リソース ファイルをマークアップのローカライズのみに使用する場合は、ファイルのプロパティ値を **\[コンテンツ\]** に変更することもできます。  詳細については、「[SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)」を参照してください。  
  
5.  各リソース ファイルを開いて、ローカライズされた文字列を追加します。その際には、各ファイルで同じ文字列 ID を使用します。  
  
6.  ASPX ページまたは ASPX コントロールの [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] マークアップで、ハードコーディングされた文字列を次の形式の値に置き換えます。  
  
    ```  
    <%$Resources:Resource File Name, String ID%>  
    ```  
  
     アプリケーション ページのラベル コントロールのテキストをローカライズする場合の例を次に示します。  
  
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
  
     ローカライズされた文字列がアプリケーションに表示されます。  ローカライズされたリソースを表示するには、リソース ファイルのカルチャに対応する Language Pack が SharePoint サーバーにインストールされている必要があります。  
  
## 参照  
 [SharePoint ソリューションのローカライズ](../sharepoint/localizing-sharepoint-solutions.md)   
 [方法: フィーチャーをローカライズする](../sharepoint/how-to-localize-a-feature.md)   
 [方法: リソース ファイルを追加する](../sharepoint/how-to-add-a-resource-file.md)   
 [方法: コードをローカライズする](../sharepoint/how-to-localize-code.md)  
  
  