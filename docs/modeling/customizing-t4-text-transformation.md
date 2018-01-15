---
title: "T4 テキスト変換のカスタマイズ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 56eb5c11984e60e16374853ef1911ae831476d64
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="customizing-t4-text-transformation"></a>T4 テキスト変換のカスタマイズ
テキスト テンプレートの機能は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]を使用するプログラム コードまたは他の変換処理を使用してテキスト ファイルを生成します。 使用して[!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]、テキスト テンプレート ディレクティブ プロセッサまたはテキスト テンプレート ホストをカスタマイズすることで、既定のテンプレート変換プロセスを拡張することができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)  
 テキスト変換のしくみについて説明しますと、テンプレート ホストとディレクティブ プロセッサの役割について説明します。  
  
 [カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 など、処理、テンプレート内のディレクティブとディレクティブ プロセッサ`<#@template#>.`テンプレートのコンパイル時に実行され、アセンブリおよびその他のリソースを読み込むことができます。 実行時にリソースを読み込むコードを挿入することもできます。 ディレクティブ プロセッサを定義するは、テンプレートの複雑さを軽減できます。  
  
 [VS 拡張機能内でのテキスト変換の呼び出し](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 作成している場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張メニュー コマンドまたはイベント ハンドラーなど、拡張機能できます使用して、テキスト テンプレート サービスを任意のテキスト テンプレートを変換します。 セッション オブジェクトを使用して、テンプレートにパラメーターのデータを渡すしを使用してから、テンプレート内の値を取得することができます、`<#@parameter#>`ディレクティブです。  
  
 [カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 テキスト テンプレートのコードを実行すると、ホストは外部のファイルおよびアプリケーションの状態へのアクセスを提供します。 テキスト変換を実行しているホストなど、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソリューション エクスプ ローラーへのアクセスを提供できます。 エラーは、エラー メッセージ ウィンドウにも表示されます。 さまざまなコンテキストでテキスト変換を実行する場合は、そのコンテキストで使用できるサービスへのアクセスを提供する、独自のホストを定義できます。  
  
 作成している場合、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]拡張機能を独自のホストを記述する代わりに、既存のテキスト変換サービスの使用を検討します。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)です。  
  
## <a name="reference"></a>参照  
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)  
  
 テキスト テンプレートのディレクティブとコントロール ブロックの構文を提供します。