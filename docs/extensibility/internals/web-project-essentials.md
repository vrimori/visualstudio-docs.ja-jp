---
title: Web プロジェクト Essentials |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a18ee19755e79c03bb24104cb444af8168307d17
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53826573"
---
# <a name="web-project-essentials"></a>Web プロジェクトの基本情報
Web プロジェクトでは、Web アプリケーションを作成します。 Web プロジェクトを使用して、スマート Web ページを含む Web アプリケーションを作成することができます。 スマート Web ページには、オンデマンドの Web ページをレンダリングするサーバー側コードがあります。  
  
 などの従来のプログラミング言語を使用して[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]または[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]、スマートの Web ページを収集し、ユーザーから情報を処理して、データベースに格納などを作成することができます。  
  
- 分離コード モデルでは、ファイル拡張子の .aspx、.asmx Web ページに依存するソース コード ファイルを関連付けます。 たとえば、依存するソース コード ファイルの hello.aspx.cs hello.aspx もあります。  
  
- スマート Web ページに関連付けられたサーバー側コードは、Web サイトの/bin フォルダーにある実行可能ファイルにコンパイルされます。  
  
- 特定の Web ページに関連付けられていないヘルパー クラスなど、追加のソース コード ファイルについては、Web サイトの場合は/App_Code フォルダーにあります。  
  
  -   Web サイト プロジェクト (WSP) には、各スマート Web ページの 1 つの実行可能ファイルが生成されます。 場合は/App_Code フォルダー内のソース コード ファイルから追加の実行可能ファイルが生成されます。  
  
  -   Web アプリケーション プロジェクト (WAP) は、コードでは、スマートのすべての Web ページと/App_Code フォルダー内のすべてのソース ファイルを 1 つの実行可能ファイルを生成します。  
  
- Web プロジェクトのソリューション ファイルは、Web サイト自体から個別に配置されています。 既定では、ソリューションのファイルは、\Documents and Settings\\*YourAccount*\My Documents\\*\<Visual Studio ### >* \Projects\\ *YourWebSite*します。  
  
  > [!NOTE]
  >  Web サイトとソリューション ファイルを保持する場合だけが移動をもう一度開きます。  
  
- Visual Studio でソリューション ファイルを持たない Web サイトを開くと、その新しいソリューション ファイルが自動的に生成します。  
  
- Web プロジェクトには、プロジェクト ファイルはあるありません。 プロジェクトの情報は、ソリューション ファイル、web.config ファイル、および他の場所に格納されます。  
  
- Web プロジェクトに自動的にグローバル プロパティを追加すると、Web プロジェクトのソリューション フォルダーに、ストレージ ファイルが作成されます。  
  
- ページ ディレクティブを使用してスマート Web ページがサーバー側のプログラミング言語と関連付けができる、または\<スクリプトの runat ="server"> タグです。  
  
- さらに、Web ページには、任意のスクリプト言語で記述されたクライアント側スクリプト ブロックの任意の数を持つことができます。  
  
- プロジェクトと項目テンプレートと登録を追加して Web サイト プロジェクト システムを実装、[!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]プロジェクト。  
  
- WAP システムは、プロジェクト フレーバーとも呼ばれる、プロジェクトのサブタイプとして実装されます。 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)]プロジェクトは、WAP システムを作成する WAP サブタイプによってフレーバーします。 プロジェクト サブタイプの詳細については、次を参照してください。[プロジェクト サブタイプ](../../extensibility/internals/project-subtypes.md)します。  
  
- スマート Web ページは、サーバー側のプログラミング言語と HTML を結合します。 サーバー側の言語には、含まれている言語が呼び出されます。 含まれている言語をサポートするために、Web プロジェクト システムを実装する必要があります、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage>インターフェイスのファミリです。  
  
  -   エディターで含まれている言語をサポートするために含まれている言語サービスに含まれている言語コードを表示する HTML の言語サービスを延期する必要があります。  
  
  -   エラーのマーカー (赤い波形) は、コード エディターのプライマリ バッファーで常に作成する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Web プロジェクト](../../extensibility/internals/web-projects.md)