---
title: "Web プロジェクトの基礎 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "web プロジェクトで essentials"
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Web プロジェクトの基礎
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Web プロジェクトでは、Web アプリケーションを作成します。 Web プロジェクトを使用すると、Web アプリケーションがスマート Web ページを作成します。 スマート Web ページでは、オンデマンドで Web ページをレンダリングするサーバー側コードを持っています。  
  
 などの従来のプログラミング言語を使用して [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] または [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], を収集、ユーザーから情報を処理し、データベースに格納、および具合スマートの Web ページを作成することができます。  
  
-   分離コード モデルでは、ファイル拡張子 .aspx、.asmx を含む Web ページに依存するソース コード ファイルを関連付けます。 たとえば、hello.aspx が依存するソース コード ファイル hello.aspx.cs 場合があります。  
  
-   スマート Web ページに関連付けられているサーバー側のコードは、Web サイトの/bin フォルダーに配置されている実行可能ファイルにコンパイルされます。  
  
-   追加のソース コード ファイルの特定の Web ページに関連付けられていないヘルパー クラスなどは、Web サイト/App_Code フォルダーに配置されます。  
  
    -   Web サイト プロジェクト (WSP) では、各スマート Web ページの 1 つの実行可能ファイルを生成します。 その他の実行可能ファイルは/App_Code フォルダー内のソース コード ファイルから生成されます。  
  
    -   Web アプリケーション プロジェクト (WAP) は、すべてのスマート Web ページとして/App_Code フォルダー内のすべてのソース ファイル、コードを組み合わせた 1 つの実行可能ファイルを生成します。  
  
-   Web プロジェクトのソリューション ファイルは、Web サイト自体からとは別に検索されます。 既定では、ソリューションのファイルは、\Documents and 設定\\*YourAccount*\My Documents\\*\< Visual Studio ### >*\Projects\\*YourWebSite*します。  
  
    > [!NOTE]
    >  Web サイトとソリューション ファイルを保持する場合は、単が移動をもう一度開きます。  
  
-   Visual Studio でソリューション ファイルを持たない Web サイトを開くと、その新しいソリューション ファイルが自動的に生成します。  
  
-   Web プロジェクトである、プロジェクト ファイルはありません。 プロジェクトの情報は、ソリューション ファイル、web.config ファイル、およびその他の場所に格納されます。  
  
-   Web プロジェクトへのグローバル プロパティを追加すると、自動的に、記憶域ファイルが Web プロジェクトのソリューション フォルダーを作成します。  
  
-   スマート Web ページに関連付けることにより、サーバー側のプログラミング言語、Page ディレクティブを使用して、または \< スクリプト runat ="server"> タグ。  
  
-   さらに、Web ページには、任意の数の任意のスクリプト言語で記述されたクライアント側スクリプト ブロックがあります。  
  
-   プロジェクトおよび項目テンプレートと登録を追加して Web サイト プロジェクト システムが実装されている、 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] プロジェクトです。  
  
-   WAP システムは、プロジェクト フレーバーとも呼ばれます。 プロジェクトのサブタイプとして実装されます。  [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] WAP システムを作成する WAP サブタイプによってプロジェクトがフレーバーします。 プロジェクトの詳細については、次を参照してください。 [プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
-   スマート Web ページは、サーバー側のプログラミング言語と HTML を結合します。 サーバー側の言語には、格納されている言語は呼び出されます。 Web プロジェクト システムを実装する必要が含まれている言語をサポートするために、 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> インターフェイスのファミリです。  
  
    -   エディターで格納されている言語をサポートするために含まれている言語サービスに含まれている言語のコードを表示する HTML 言語サービスを延期する必要があります。  
  
    -   エラー マーカー (赤い波形) は、常に、コード エディターのプライマリ バッファーに作成する必要があります。  
  
## <a name="see-also"></a>参照  
 [Web プロジェクト](../../extensibility/internals/web-projects.md)