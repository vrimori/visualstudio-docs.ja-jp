---
title: Web プロジェクト Essentials |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6918c539409a31dfe5249adb5858ca20c8c2337c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="web-project-essentials"></a>Web プロジェクトの基礎
Web プロジェクトでは、Web アプリケーションを作成します。 Web プロジェクトを使用して、Web アプリケーションに含まれるスマートの Web ページを作成することができます。 スマート Web ページには、要求時に Web ページを表示するサーバー側コードがあります。  
  
 などの従来のプログラミング言語を使用して[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]または[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]、収集プロセスのユーザーから情報をデータベースに格納し、スマートの Web ページを作成することができます。  
  
-   分離コード モデルでは、ファイル拡張子の .aspx、.asmx Web ページに依存するソース コード ファイルを関連付けます。 たとえば、hello.aspx が依存するソース コード ファイル hello.aspx.cs 場合があります。  
  
-   スマート Web ページに関連付けられているサーバー側のコードは、Web サイト/bin フォルダーに配置されている実行可能ファイルにコンパイルされます。  
  
-   特定の Web ページに関連付けられていないヘルパー クラスなど、追加のソース コード ファイルは、Web サイトの場合は/App_Code フォルダーにあります。  
  
    -   Web サイト プロジェクト (WSP) は、各スマート Web ページの 1 つの実行可能ファイルを生成します。 場合は/App_Code フォルダー内のソース コード ファイルから追加の実行可能ファイルが生成されます。  
  
    -   Web アプリケーション プロジェクト (WAP) は、スマートのすべての Web ページだけでなく場合は/App_Code フォルダー内のすべてのソース ファイルのコードを結合する 1 つの実行可能ファイルを生成します。  
  
-   Web プロジェクトのソリューション ファイルが Web サイト自体から個別に配置します。 既定では、ソリューションのファイルは、\Documents and 設定\\*自分のアカウント*\My Documents\\*\<Visual Studio ### >*\Projects\\ *YourWebSite*です。  
  
    > [!NOTE]
    >  Web サイトとソリューション ファイルを保持する場合は、だけその場所に移動し、ウィンドウを開きます。  
  
-   Visual Studio でソリューション ファイルを持たない Web サイトを開くと、その新しいソリューション ファイルが自動的に生成します。  
  
-   プロジェクト ファイルがある web プロジェクトがありません。 プロジェクトの情報は、ソリューション ファイル、web.config ファイル、およびその他の場所に格納されます。  
  
-   Web プロジェクトへのグローバル プロパティを自動的に追加すると、Web プロジェクトのソリューション フォルダーに記憶域ファイルが作成されます。  
  
-   スマート Web ページはページ ディレクティブを使用してサーバー側のプログラミング言語に関連付けできるまたは\<スクリプト runat ="server"> タグです。  
  
-   さらに、Web ページには、任意のスクリプト言語で記述されたクライアント側スクリプト ブロックの任意の数を持つことができます。  
  
-   プロジェクトと項目テンプレートと登録を追加して Web サイト プロジェクト システムが実装されている、[!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]プロジェクト。  
  
-   WAP システムは、プロジェクト フレーバーとも呼ばれる、プロジェクトのサブタイプとして実装されます。 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] WAP サブタイプ WAP システムを作成するでプロジェクトをフレーバーします。 プロジェクトのサブタイプの詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)です。  
  
-   スマート Web ページは、サーバー側のプログラミング言語と HTML を結合します。 サーバー側の言語には、格納されている言語が呼び出されます。 格納されている言語をサポートするために、Web プロジェクト システムを実装する必要があります、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイスのファミリです。  
  
    -   エディターで、格納されている言語をサポートするために含まれている言語サービスに格納されている言語コードを表示する HTML 言語サービスを延期する必要があります。  
  
    -   エラー マーカー (赤い波形) は、常に、コード エディターのプライマリ バッファーに作成する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Web プロジェクト](../../extensibility/internals/web-projects.md)