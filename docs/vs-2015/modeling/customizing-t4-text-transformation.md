---
title: T4 テキスト変換のカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e304b38979b80c1d67d3f88accdbfa584406c9cb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547851"
---
# <a name="customizing-t4-text-transformation"></a>T4 テキスト変換のカスタマイズ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[T4 テキスト変換のカスタマイズ](https://docs.microsoft.com/visualstudio/modeling/customizing-t4-text-transformation)します。  
  
テキスト テンプレートの機能は、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プログラム コードまたは変換プロセスには、その他のテキスト ファイルを生成することができます。 使用して[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]、テキスト テンプレート ディレクティブ プロセッサまたはテキスト テンプレート ホストをカスタマイズすることで、既定のテンプレートの変換プロセスを拡張することができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)  
 テキスト変換のしくみについて説明しますと、テンプレートのホストとディレクティブ プロセッサの役割について説明します。  
  
 [カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 ディレクティブ プロセッサの処理、テンプレートのディレクティブを使用してなど`<#@template#>.`テンプレートのコンパイル時に実行され、アセンブリとその他のリソースを読み込むことができます。 実行時にリソースを読み込むコードを挿入することもできます。 ディレクティブ プロセッサを定義することでは、テンプレートの複雑さを軽減できます。  
  
 [VS 拡張機能内でのテキスト変換の呼び出し](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 作成する場合、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]メニュー コマンドまたはイベント ハンドラーなどの拡張機能は、拡張機能できますを使用して、テキスト テンプレート サービスを任意のテキスト テンプレートを変換します。 セッション オブジェクトを使用して、テンプレートにパラメーターのデータを渡すし、を使用して、テンプレート内から値を取得することができます、`<#@parameter#>`ディレクティブ。  
  
 [カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 テキスト テンプレートのコードを実行すると、ホストは外部のファイルとアプリケーションの状態へのアクセスを提供します。 テキスト変換を実行するホストなど[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ソリューション エクスプ ローラーにアクセスできるようにします。 エラーは、エラー メッセージ ウィンドウにも表示されます。 別のコンテキストでテキスト変換を実行する場合は、そのコンテキストで使用可能なサービスへのアクセスを提供する、独自のホストを定義できます。  
  
 作成する場合、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]拡張機能で、独自のホストを記述する代わりに、既存のテキスト変換サービスの使用を検討します。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)します。  
  
## <a name="reference"></a>参照  
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)  
  
 テキスト テンプレートのディレクティブとコントロール ブロックの構文について説明します。



