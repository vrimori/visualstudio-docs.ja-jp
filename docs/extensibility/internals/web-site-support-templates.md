---
title: Web サイトのサポート テンプレート |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36c22cbb5ca39e48e488851f26786955c9704fda
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961599"
---
# <a name="web-site-support-templates"></a>Web サイト サポートのテンプレート
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Web サイト プロジェクトと項目テンプレートは、新しい Web サイト プロジェクトと項目を最初から作成する必要はありませんが、開発プロセスを加速する再利用可能かつカスタマイズ可能な Web サイト プロジェクトと項目スタブを提供します。 詳細については[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]テンプレートを参照してください[を作成するプロジェクトと項目テンプレート](../../ide/creating-project-and-item-templates.md)します。

## <a name="project-template-folder"></a>プロジェクト テンプレート フォルダー
 Web プロジェクト テンプレートは、通常のインストール [*Visual Studio インストール パス*] \Common7\IDE\ProjectTemplates\Web\\、各プログラミング言語 web 後という名前のサブフォルダーにします。

## <a name="project-file"></a>プロジェクト ファイル
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) では、適切なプロジェクトの種類にテンプレートをマップする方法としてプロジェクト ファイルの拡張子が必要です。 Web プロジェクトはプロジェクト ファイルがあるないために、ダミーのプロジェクト ファイルの拡張機能の .webproj はプロジェクトの種類に、テンプレートをマップに登録されます。

 言語名の文字列を追加して既定の言語を設定する Web プロジェクト システムを有効にする、テンプレートに、必要に応じて、**新しい項目の追加**テンプレートに基づいて項目のダイアログ ボックス。 文字列は、ファイルの最初の行である必要があります。 IntelliSense エンジンの登録で AddItemLanguageName 登録の名前とプロジェクト Subtype(VsTemplate) の下に登録名の両方に一致する必要があります。 詳細については、次を参照してください。 [Web サイト サポート属性](../../extensibility/internals/web-site-support-attributes.md)します。

 文字列が存在しない場合、Web プロジェクト システムは、プロジェクト テンプレートによって Web プロジェクトに追加されたページの言語の属性とファイル拡張機能に基づく既定の言語を決定しようとします。

## <a name="project-templates"></a>プロジェクト テンプレート
 Web サイト プロジェクトのテンプレートへの応答で新しい Web サイトの構築に使用されます、**新しい Web サイト**コマンドを**ファイル**メニュー。 次の 3 つの Web サイト プロジェクトの種類は現在サポートされています。

-   空の Web サイト プロジェクト

-   Web サイト プロジェクト

-   Web サービス プロジェクト

### <a name="empty-web-site-projects"></a>空の Web サイト プロジェクト
 これらのファイルへの応答で新しい空の Web サイトの作成、**空の Web サイト**コマンドで、選択した後は**ファイル** > **新しい Web サイト**:

-   EmptyWeb.vstemplate

     新しい空の Web サイトの作成の指針、テンプレート ファイル。

-   EmptyWeb.webproj

     このファイルは、プロジェクト テンプレートのシステムの成果物です。 EmptyWeb.vstemplate ファイルで、プロジェクト ファイルの参照を満たしています。

### <a name="web-site-projects"></a>Web サイト プロジェクト
 これらのファイルへの応答で新しい Web サイトの作成、 **ASP.NET Web サイト**コマンドで、選択した後は**ファイル** > **新しい Web サイト**:

-   Default.aspx

     新しい Web サイトの既定のホーム ページ。 言語属性は、分離コード言語を指定し、CodeFile 属性は、このページに関連付けられた分離コードを格納している依存ファイルを指定します。

-   Default.aspx です。*拡張機能*

     既定のホーム ページの分離コードを含む依存ファイル。 分離コード言語の決定、*拡張子*このファイルの。

-   web.config

     ルート web.site 構成ファイル。

-   WebApplication.vstemplate

     Web サイト ソリューションの内容を決定し、強制的に App_Data フォルダーを作成するテンプレート ファイルです。

-   WebApplication.webproj

     このファイルは、プロジェクト テンプレートのシステムの成果物です。 WebApplication.vstemplate ファイルで、プロジェクト ファイルの参照を満たしています。

### <a name="web-service-projects"></a>Web サービス プロジェクト
 これらのファイルへの応答で新しい Web サイトの作成、 **ASP.NET Web サービス**コマンドで、選択した後は**ファイル** > **新しい Web サイト**:

-   Service.asmx

     新しい Web サービスの HTML ページ。 言語属性を分離コード言語を指定し、分離コード属性は、このサービスに関連付けられた分離コードを含む依存ファイルを指定します。

-   サービス。 *extension*

     サービス クラスを実装する依存ファイル。 分離コード言語の決定、*拡張子*このファイルの。

-   web.config

-   ルート web.site 構成ファイル。

-   WebService.vstemplate

     Web サイト ソリューションのコンテンツを決定し、App_Data、App_Code フォルダーの作成を強制するテンプレート ファイルです。 サービスです。*拡張子*ファイルが App_Code フォルダーにコピーされます。

-   WebService.webproj

     このファイルは、プロジェクト テンプレートのシステムの成果物です。 WebService.vstemplate ファイルで、プロジェクト ファイルの参照を満たしています。

## <a name="project-item-template-folder"></a>プロジェクト アイテム テンプレート フォルダー
 Web プロジェクト項目テンプレートは、通常のインストール [*Visual Studio インストール パス*] \Common7\IDE\ItemTemplates\Web\\、各プログラミング言語の web にちなんだ名前のサブフォルダーにします。

## <a name="project-item-templates"></a>プロジェクト項目テンプレート
 Web サイト プロジェクト項目テンプレートを使用して Web サイトへの応答に新しい Web ページを追加する、**既存項目の追加**コマンド。 この種の Web ページは現在サポートされています。

-   新しいクラス

-   新しい HTML ページ

-   新しい Web フォーム

-   新しいマスター ページ

### <a name="new-class"></a>新しいクラス
 このテンプレートへの応答で空のクラスを定義する新しいソース ファイルの作成、**新しいクラスの追加**コマンド。

-   クラス。 *extension*

     空のクラスを実装するソース ファイル。 分離コード言語の決定、*拡張子*このファイルの。

-   Class.vstemplate

     テンプレート ファイル、ソース ファイルを作成し、その内容を決定します。

### <a name="new-html-page"></a>新しい HTML ページ
 このテンプレートへの応答で新しい Web ページを作成、**新しい HTML ページの追加**コマンド。

-   HTMLPage.htm

     Web ページのコンテンツの開始。 通常、この Web ページには関連する分離コードの依存ファイルがありません。 関連の分離コード ファイルを使用したスマートのページを作成するには、代わりに、Web フォーム テンプレートを使用します。

-   HTMLPage.vstemplate

     テンプレート ファイルを Web ページを作成し、その内容を決定します。

### <a name="new-webform"></a>新しい web フォーム
 このテンプレートへの応答で新しいスマート Web ページを作成、**新しい Web フォームの追加**コマンド。

 依存の分離コードのソース ファイルを作成するには、選択**別のファイルにコードを配置**します。 空のスクリプト ブロックと no を持つ単一の Web ページが作成された場合は、\<ページ % % > 依存ファイルをフックするディレクティブ。

 選択したマスター ページのコンテンツ ページを作成するには、選択**マスター ページを選択**します。

-   WebForm.aspx

     Web ページのコンテンツの開始。 この Web ページには、関連する分離コードの依存ファイルがありません。

-   WebForm_cb.aspx

     Web ページのコンテンツの開始。 この Web ページでは、関連する分離コードの依存ファイルにします。

-   分離コード。 *extension*

     Web フォーム クラスを実装する依存ファイル。 分離コード言語の決定、*拡張子*このファイルの。

-   ContentPage.aspx

     コンテンツ ページとして Web ページのコンテンツの開始。 この Web ページには、関連する分離コードの依存ファイルがありません。

-   ContentPage_cb.aspx

     コンテンツ ページとして Web ページのコンテンツの開始。 この Web ページでは、関連する分離コードの依存ファイルにします。

-   WebForm.vstemplate

     存在する場合は、新しい web ページとその依存ファイルの内容を決定するテンプレート ファイル。

### <a name="new-master-page"></a>新しいマスター ページ
 このテンプレートへの応答で新しいマスター ページを作成、**新しいマスター ページの追加**コマンド。

 依存の分離コードのソース ファイルを作成するには、選択**別のファイルにコードを配置**します。 空のスクリプト ブロックと no を持つ単一の Web ページが作成されるそれ以外の場合\<ページ % % > 依存ファイルをフックするディレクティブ。

-   MasterPage.master

     マスター ページのコンテンツの開始。 このマスター ページには、関連する分離コードの依存ファイルがありません。

-   MasterPage_cb.master

     マスター ページのコンテンツの開始。 このマスター ページには、関連する分離コードの依存ファイルがあります。

-   分離コード。*拡張機能*

     マスター ページ クラスを実装する依存ファイル。 分離コード言語の決定、*拡張子*このファイルの。

-   MasterPage.vstemplate

     存在する場合は、新しいマスター ページとその依存ファイルの内容を決定するテンプレート ファイル。

## <a name="see-also"></a>関連項目
 [Web サイト サポート](../../extensibility/internals/web-site-support.md)