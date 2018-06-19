---
title: Web サイトのサポート テンプレート |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af8e0d845157b475e4a5527443f55286828023cc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31147129"
---
# <a name="web-site-support-templates"></a>Web サイト テンプレートをサポート
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Web サイトのプロジェクトと項目テンプレートは、最初から新しい Web サイト プロジェクトと項目を作成する必要性を解消して、開発プロセスを高速化と再利用可能なカスタマイズ可能な Web サイトのプロジェクトと項目のスタブを提供します。 詳細については[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、テンプレートを参照してください[を作成するプロジェクトと項目テンプレート](../../ide/creating-project-and-item-templates.md)です。

## <a name="project-template-folder"></a>プロジェクト テンプレート フォルダー
 Web プロジェクト テンプレートは、通常のインストール [*Visual Studio インストール パス*] \Common7\IDE\ProjectTemplates\Web\\、web プログラミング言語にちなんだ名前のサブフォルダーでは、それぞれします。

## <a name="project-file"></a>プロジェクト ファイル
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) では、適切なプロジェクトの種類にテンプレートをマップする方法としてプロジェクト ファイルの拡張子が必要です。 Web プロジェクトには、プロジェクト ファイルがない、ダミーのプロジェクト ファイルの拡張子 .webproj が登録されているため、テンプレート、プロジェクトの種類をマップします。

 言語名の文字列を追加してで既定の言語を設定する Web プロジェクト システムを有効にする、テンプレートに、必要に応じて、**新しい項目の追加**テンプレートに基づいて項目 ダイアログ ボックス。 文字列は、ファイルの最初の行である必要があります。 IntelliSense エンジン登録で AddItemLanguageName 下にある登録の名前とプロジェクト Subtype(VsTemplate) の下に登録名の両方に一致する必要があります。 詳細については、次を参照してください。 [Web サイト サポート属性](../../extensibility/internals/web-site-support-attributes.md)です。

 文字列が存在しない場合、Web プロジェクト システムは、プロジェクト テンプレートによって、Web プロジェクトに追加されたページの言語の属性とファイル拡張機能に基づく既定の言語を決定しようとします。

## <a name="project-templates"></a>プロジェクト テンプレート
 Web サイト プロジェクト テンプレートがへの応答で新しい Web サイトの構築に使用される、**新しい Web サイト**コマンドを**ファイル**メニュー。 次の 3 つの Web サイト プロジェクトの種類は現在サポートされています。

-   空の Web サイト プロジェクト

-   Web サイト プロジェクト

-   Web サービス プロジェクト

### <a name="empty-web-site-projects"></a>空の Web サイト プロジェクト
 これらのファイルへの応答で新しい空の Web サイトを作成する、**空の Web サイト**コマンドでは、選択した後にある**ファイル** > **新しい Web サイト**:

-   EmptyWeb.vstemplate

     テンプレート ファイルを新しい空の Web サイトの作成手順について説明します。

-   EmptyWeb.webproj

     このファイルは、プロジェクト テンプレートのシステムの成果物です。 EmptyWeb.vstemplate ファイル内のプロジェクト ファイルの参照を満たします。

### <a name="web-site-projects"></a>Web サイト プロジェクト
 これらのファイルへの応答で新しい Web サイトを作成する、 **ASP.NET Web サイト**コマンドでは、選択した後にある**ファイル** > **新しい Web サイト**:

-   Default.aspx

     新しい Web サイトの既定のホーム ページです。 言語属性は、分離コード言語を指定し、CodeFile 属性がこのページに関連付けられている分離コードを格納している依存ファイルを指定します。

-   Default.aspx です。*拡張機能*

     依存ファイルが既定のホーム ページの分離コードが含まれています。 分離コード言語の決定、*拡張子*このファイルのです。

-   web.config

     ルート web.site 構成ファイル。

-   WebApplication.vstemplate

     Web サイトのソリューションの内容を決定し、強制的に App_Data フォルダーを作成するテンプレート ファイルです。

-   WebApplication.webproj

     このファイルは、プロジェクト テンプレートのシステムの成果物です。 WebApplication.vstemplate ファイル内のプロジェクト ファイルの参照を満たします。

### <a name="web-service-projects"></a>Web サービス プロジェクト
 これらのファイルへの応答で新しい Web サイトを作成する、 **ASP.NET Web サービス**コマンドでは、選択した後にある**ファイル** > **新しい Web サイト**:

-   Service.asmx

     新しい Web サービスの HTML ページです。 Language 属性が、分離コード言語を指定し、分離コード属性は、このサービスに関連付けられている分離コードを格納している依存ファイルを指定します。

-   サービス。 *extension*

     サービス クラスを実装する依存ファイル。 分離コード言語の決定、*拡張子*このファイルのです。

-   web.config

-   ルート web.site 構成ファイル。

-   WebService.vstemplate

     テンプレート ファイルを Web サイトのソリューションの内容を確認し、強制的に、App_Data、App_Code フォルダーを作成します。 サービスです。*拡張子*ファイルが App_Code フォルダーにコピーします。

-   WebService.webproj

     このファイルは、プロジェクト テンプレートのシステムの成果物です。 WebService.vstemplate ファイル内のプロジェクト ファイルの参照を満たします。

## <a name="project-item-template-folder"></a>プロジェクト項目テンプレート フォルダー
 Web プロジェクト項目テンプレートは、通常のインストール [*Visual Studio インストール パス*] \Common7\IDE\ItemTemplates\Web\\、その web プログラミング言語にちなんだ名前のサブフォルダーでは、それぞれします。

## <a name="project-item-templates"></a>プロジェクト項目テンプレート
 Web サイト プロジェクト項目テンプレートを使用して Web サイトへの応答に新しい Web ページを追加する、**既存項目の追加**コマンド。 これらの Web ページは現在サポートされています。

-   新しいクラス

-   新しい HTML ページ

-   新しい Web フォーム

-   新しいマスター ページ

### <a name="new-class"></a>新しいクラス
 このテンプレートを作成、新しいソース ファイルへの応答で空のクラスを定義する、**新しいクラスの追加**コマンド。

-   クラス。 *extension*

     空のクラスを実装するソース ファイル。 分離コード言語の決定、*拡張子*このファイルのです。

-   Class.vstemplate

     テンプレート ファイルをソース ファイルを作成し、その内容を決定します。

### <a name="new-html-page"></a>新しい HTML ページ
 このテンプレートへの応答で新しい Web ページを作成、**新しい HTML ページの追加**コマンド。

-   HTMLPage.htm

     Web ページのコンテンツの開始。 通常この Web ページには関連する分離コードの依存ファイルがありません。 関連する分離コード ファイルを使用してスマート ページを作成するには、代わりに、Web フォーム テンプレートを使用します。

-   HTMLPage.vstemplate

     テンプレート ファイルを Web ページを作成し、その内容を決定します。

### <a name="new-webform"></a>新しい web フォーム
 このテンプレートへの応答で新しいスマート Web ページを作成、**新しい Web フォームの追加**コマンド。

 依存する分離コードのソース ファイルを作成するには、選択**別のファイルにコードを配置**です。 空のスクリプト ブロックといいえを持つ単一の Web ページが作成されたそれ以外の場合、 \<% ページ % > ディレクティブを依存ファイルをフックするためです。

 選択したマスター ページのコンテンツ ページを作成するには、選択**マスター ページを選択**です。

-   WebForm.aspx

     Web ページのコンテンツの開始。 この Web ページには、関連する分離コードの依存ファイルがありません。

-   WebForm_cb.aspx

     Web ページのコンテンツの開始。 この Web ページは、関連する分離コードの依存ファイルがします。

-   分離コード。 *extension*

     Web フォーム クラスを実装する依存ファイル。 分離コード言語の決定、*拡張子*このファイルのです。

-   ContentPage.aspx

     コンテンツ ページとして Web ページのコンテンツの開始。 この Web ページには、関連する分離コードの依存ファイルがありません。

-   ContentPage_cb.aspx

     コンテンツ ページとして Web ページのコンテンツの開始。 この Web ページは、関連する分離コードの依存ファイルがします。

-   WebForm.vstemplate

     存在する場合は、新しい web ページとその依存ファイルの内容を決定するテンプレート ファイル。

### <a name="new-master-page"></a>新しいマスター ページ
 このテンプレートでは、新しいマスター ページを作成への応答、**新しいマスター ページの追加**コマンド。

 依存する分離コードのソース ファイルを作成するには、選択**別のファイルにコードを配置**です。 空のスクリプト ブロックといいえを持つ単一の Web ページが作成されたそれ以外の場合\<% ページ % > ディレクティブを依存ファイルをフックするためです。

-   MasterPage.master

     マスター ページのコンテンツの開始。 このマスター ページには、関連する分離コードの依存ファイルがありません。

-   MasterPage_cb.master

     マスター ページのコンテンツの開始。 このマスター ページには、関連する分離コードの依存ファイルがあります。

-   分離コード。*拡張機能*

     マスター ページ クラスを実装する依存ファイル。 分離コード言語の決定、*拡張子*このファイルのです。

-   MasterPage.vstemplate

     存在する場合は、新しいマスター ページとその依存ファイルの内容を決定するテンプレート ファイル。

## <a name="see-also"></a>関連項目
 [Web サイト サポート](../../extensibility/internals/web-site-support.md)