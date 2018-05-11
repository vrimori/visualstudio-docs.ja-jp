---
title: 単一ファイル ジェネレーターの実装 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 71db8036634cfc266db3c585c48317262f48b367
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="implementing-single-file-generators"></a>単一ファイル ジェネレーターの実装
カスタム ツール — 単一ファイル ジェネレーターとも呼ば — 拡張に使用できる、[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]と[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]プロジェクト システムで[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 カスタム ツールは、実装する COM コンポーネント、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>インターフェイスです。 このインターフェイスを使用して、カスタム ツールは、1 つの出力ファイルに 1 つの入力ファイルを変換します。 役立つその他の出力または変換の結果は、ソース コードにあります。 カスタム ツールで生成されたコード ファイルの 2 つの例は、ビジュアル デザイナーや Web サービス記述言語 (WSDL) を使用して生成されたファイルの変更に応答で生成されたコードです。  
  
 プロジェクト システムが呼び出されて、カスタム ツールが読み込まれると、入力ファイルが保存される際、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>メソッドへの参照を渡すと、<xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>ツールが、ユーザーに進行状況を報告するためのコールバック インターフェイス。  
  
 カスタム ツールを生成する出力ファイルは、入力ファイルに依存して、プロジェクトに追加されます。 プロジェクト システムのカスタム ツールの実装によって返される文字列に基づいて、出力ファイルの名前を自動的に決定する<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>です。  
  
 カスタム ツールを実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>インターフェイスです。 必要に応じて、カスタム ツールのサポート、<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>入力ファイル以外のソースから情報を取得するインターフェイスです。 いずれの場合は、カスタム ツールを使用することができます、前に登録すると、システム、または、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ローカル レジストリです。 カスタム ツールを登録する方法の詳細については、次を参照してください。[単一ファイル ジェネレーターの登録](../../extensibility/internals/registering-single-file-generators.md)です。  
  
## <a name="see-also"></a>関連項目  
 [ビジュアル デザイナーへのタイプの公開](../../extensibility/internals/exposing-types-to-visual-designers.md)