---
title: "Web サイト テンプレートをサポート | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "私たちのサイトのプロジェクト テンプレート"
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Web サイト テンプレートをサポート
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Web サイト   プロジェクトと項目テンプレートは新しい Web サイト プロジェクトおよび項目を最初から作成する必要を削除して開発プロセスを短縮する再利用できるようにカスタマイズ可能な Web サイト プロジェクトおよび項目のスタブを提供します。  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] テンプレートの詳細については[カスタム プロジェクトと項目テンプレートの作成](../../ide/creating-project-and-item-templates.md) を参照してください。  
  
## プロジェクト テンプレート フォルダー  
 Web プロジェクト テンプレートは通常テンプレートにインストール *Visual Studio のインストール パス* \[\] \\ Common7 \\ IDE \\ ProjectTemplates \\ \\ WebWeb プログラミング言語にちなんだ名前のサブフォルダーします。  
  
## プロジェクト ファイル  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の統合開発環境が \(IDE\) 正しいプロジェクトにテンプレートをマップする方法としてプロジェクト ファイルの拡張子が必要です。  Web プロジェクトにはプロジェクト ファイルがないためこれをサポートするためにダミー プロジェクト ファイルの拡張子は .webproj 登録されます。  
  
 必要に応じて言語名の文字列はテンプレートにテンプレートに基づいて項目の ENT0ENT \[出力\] ダイアログ ボックスの言語の既定値を設定しWeb プロジェクト システムができるようにするために追加できます。  文字列はファイルの最初の行でIntelliSense エンジンの登録 AddItemLanguageName の下に登録されている名前とプロジェクトのサブタイプ \(VsTemplate\) に登録されている名前の両方に一致させる必要があります。  詳細については、「[Web サイトのサポートの属性](../../extensibility/internals/web-site-support-attributes.md)」を参照してください。  
  
 文字列がない場合Web プロジェクト システムはプロジェクト テンプレートのプロジェクト テンプレートを使用して Web ページに追加された言語の属性とファイル拡張子に基づいて既定の言語が決定されます。  
  
## プロジェクト テンプレート  
 Web サイト プロジェクト テンプレートが ENT1ENT \[入力\] メニューの  **新しい Web サイト**  のコマンドに応じて新しい Web サイトを作成するために使用されます。  3 回の Web サイト プロジェクトの種類は現在はサポートされています :  
  
-   空の Web サイト プロジェクト  
  
-   Web サイト プロジェクト  
  
-   Web サービス プロジェクト  
  
### 空の Web サイト プロジェクト  
 これらのファイルは \[入力\] ENT2ENT メニューのをポイント  **新しい Web サイト**  の後で使用できる **\*\*\* Empty Web Site \*\*\*** のコマンドに応じて新しい空の Web サイトを作成します :  
  
-   EmptyWeb.vstemplate  
  
     新しい空の Web サイトを作成するテンプレート ファイル。  
  
-   EmptyWeb.webproj  
  
     このファイルはプロジェクト テンプレートのシステムの成果物です。  これは EmptyWeb.vstemplate ファイル プロジェクトのファイル参照を満たします。  
  
### Web サイト プロジェクト  
 これらのファイルは \[入力\] ENT2ENT メニューのをポイント  **新しい Web サイト**  の後で使用できる **\*\*\* ASP.NET Web Site \*\*\*** のコマンドに応じて新しい Web サイトを作成します :  
  
-   Default.aspx  
  
     新しい Web サイトの既定のホーム ページです。  Language 属性は codebehind の言語を指定しCodeFile の属性がこのページに関連付けられている codebehind コードを含む依存ファイルを指定します。  
  
-   Default.aspx. *拡張子*  
  
     既定のホーム ページの codebehind コードを含む依存ファイル。  codebehind の言語ではこのファイルの  *拡張子*  を決定します。  
  
-   web.config  
  
     構成ファイルのルート web.site。  
  
-   WebApplication.vstemplate  
  
     Web サイトのソリューションの内容を確認しApp\_Data フォルダーの作成を強制するテンプレート ファイル。  
  
-   WebApplication.webproj  
  
     このファイルはプロジェクト テンプレートのシステムの成果物です。  これは WebApplication.vstemplate ファイル プロジェクトのファイル参照を満たします。  
  
### Web サービス プロジェクト  
 これらのファイルは \[入力\] ENT2ENT メニューのをポイント  **新しい Web サイト**  の後で使用できる **ASP.NET Web サービス**  のコマンドに応じて新しい Web サイトを作成します :  
  
-   Service.asmx  
  
     新しい Web サービスの HTML ページ。  Language 属性は codebehind の言語を指定しCodeBehind 属性はこのサービスに関連付けられた codebehind コードを含む依存ファイルを指定します。  
  
-   サービス。 *拡張子*  
  
     サービスのクラスを実装する依存ファイル。  codebehind の言語ではこのファイルの  *拡張子*  を決定します。  
  
-   web.config  
  
-   構成ファイルのルート web.site。  
  
-   WebService.vstemplate  
  
     Web サイトのソリューションの内容を確認しApp\_Data と App\_Code フォルダーの作成を強制するテンプレート ファイル。  サービス。 *拡張子*  ファイルを App\_Code フォルダーにコピーします。  
  
-   WebService.webproj  
  
     このファイルはプロジェクト テンプレートのシステムの成果物です。  これは WebService.vstemplate ファイル プロジェクトのファイル参照を満たします。  
  
## プロジェクト項目テンプレート フォルダー  
 Web プロジェクト テンプレート項目テンプレート通常インストール *Visual Studio のインストール パス* \[\] \\ Common7 \\ IDE \\ ItemTemplates \\ \\ WebWeb プログラミング言語にちなんだ名前のサブフォルダーします。  
  
## プロジェクト項目テンプレート  
 Web サイトのプロジェクト項目テンプレートが  **既存項目の追加**  のコマンドによる Web サイトに新しい Web ページを追加するために使用されます。  これらの種類の Web ページは現在はサポートされています :  
  
-   新しいクラス  
  
-   新しい HTML ページ  
  
-   新しい Web フォーム  
  
-   新しいマスター ページ  
  
### 新しい Class  
 このテンプレートは **\*\*\* Add New Class \*\*\*** のコマンドに対して空のクラスを定義するソース ファイルを作成します。  
  
-   クラスです。 *拡張子*  
  
     空のクラスを実装するソース ファイル。  codebehind の言語ではこのファイルの  *拡張子*  を決定します。  
  
-   Class.vstemplate  
  
     ソース ファイルを作成し内容を確認テンプレート ファイル。  
  
### 新しい HTML ページ  
 このテンプレートは **\*\*\* Add New HTML Page \*\*\*** のコマンドに応じて新しい Web ページを作成します。  
  
-   HTMLPage.htm  
  
     Web ページのコンテンツを呼び出します。  この Web ページには関連する codebehind の依存ファイルはありません。  関連する codebehind ファイルを使用してスマート ページを作成するにはWeb フォーム テンプレートを使用します。  
  
-   HTMLPage.vstemplate  
  
     Web ページを作成しコンテンツを決定するテンプレート ファイル。  
  
### 新しい WebForm  
 このテンプレートは **\*\*\* Add New Web Form \*\*\*** のコマンドへの応答として新しいスマート Web ページを作成します。  
  
 依存 codebehind ソース ファイルを作成するには\[ENT0ENT\] を選択します。  それ以外の場合は空のスクリプト ブロックと \<% の %\> ページのディレクティブが依存ファイルをフックする単一の Web ページが作成されます。  
  
 選択されたマスター ページのコンテンツ ページを作成するには\[ENT0ENT\] を選択します。  
  
-   WebForm.aspx  
  
     Web ページのコンテンツを呼び出します。  この Web ページに関連 codebehind の依存ファイルはありません。  
  
-   WebForm\_cb.aspx  
  
     Web ページのコンテンツを呼び出します。  この Web ページに関連 codebehind の依存ファイルがあります。  
  
-   Codebehind。 *拡張子*  
  
     webform のクラスを実装する依存ファイル。  codebehind の言語ではこのファイルの  *拡張子*  を決定します。  
  
-   ContentPage.aspx  
  
     コンテンツ ページとして Web ページのコンテンツを呼び出します。  この Web ページに関連 codebehind の依存ファイルはありません。  
  
-   ContentPage\_cb.aspx  
  
     コンテンツ ページとして Web ページのコンテンツを呼び出します。  この Web ページに関連 codebehind の依存ファイルがあります。  
  
-   WebForm.vstemplate  
  
     新しい Web ページとその依存ファイルの内容を判断テンプレート ファイルです \(存在する場合\)。  
  
### 新しいマスター ページ  
 このテンプレートは **\*\*\* Add New Master Page \*\*\*** のコマンドに応じて新しいマスター ページを作成します。  
  
 依存 codebehind ソース ファイルを作成するには\[ENT0ENT\] を選択します。  それ以外の場合は空のスクリプト ブロックと \<% の %\> ページのディレクティブが依存ファイルをフックする単一の Web ページが作成されます。  
  
-   MasterPage.master  
  
     マスター ページのコンテンツの開始。  このマスター ページに関連 codebehind の依存ファイルはありません。  
  
-   MasterPage\_cb.master  
  
     マスター ページのコンテンツの開始。  このマスター ページに関連 codebehind の依存ファイルがあります。  
  
-   Codebehind。 *拡張子*  
  
     マスター ページのクラスを実装する依存ファイル。  codebehind の言語ではこのファイルの  *拡張子*  を決定します。  
  
-   MasterPage.vstemplate  
  
     新しいマスター ページとその依存ファイルの内容を判断テンプレート ファイルです \(存在する場合\)。  
  
## 参照  
 [Web サイトのサポート](../../extensibility/internals/web-site-support.md)