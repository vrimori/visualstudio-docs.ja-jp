---
title: 単一ファイル ジェネレーターの実装 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 30294f901f3e0536caeb84dc55af5630db24956a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47533390"
---
# <a name="implementing-single-file-generators"></a>単一ファイル ジェネレーターの実装
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[単一ファイル ジェネレーターの実装](https://docs.microsoft.com/visualstudio/extensibility/internals/implementing-single-file-generators)します。  
  
カスタム ツール-単一ファイル ジェネレーターとも呼ば-拡張に使用できる、[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]と[!INCLUDE[csprcs](../../includes/csprcs-md.md)]プロジェクト システムで[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]します。 カスタム ツールは、実装する COM コンポーネント、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>インターフェイス。 このインターフェイスを使用して、カスタム ツールは、1 つの出力ファイルに 1 つの入力ファイルを変換します。 変換の結果には、ソース コードが可能性があります。 または役立つその他の出力します。 カスタム ツールで生成されたコード ファイルの 2 つの例は、ビジュアル デザイナーと Web サービス記述言語 (WSDL) を使用して生成されたファイルの変更に応答で生成されたコードです。  
  
 カスタム ツールが読み込まれると、入力ファイルが保存される際、プロジェクト システムを呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>メソッドへの参照を渡すと、<xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>ツールがユーザーにその進行状況を報告するためのコールバック インターフェイス。  
  
 カスタム ツールを生成する出力ファイルは、入力ファイルへの依存関係をプロジェクトに追加されます。 プロジェクト システムのカスタム ツールの実装によって返される文字列に基づいて、出力ファイルの名前を自動的に決定する<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>します。  
  
 カスタム ツールを実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>インターフェイス。 必要に応じて、カスタム ツールのサポート、<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>インターフェイスは、入力ファイル以外のソースから情報を取得します。 いずれの場合も、カスタム ツールを使用する前に登録すると、システムまたは、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ローカル レジストリ。 カスタム ツールを登録する方法の詳細については、次を参照してください。[単一ファイル ジェネレーターの登録](../../extensibility/internals/registering-single-file-generators.md)します。  
  
## <a name="see-also"></a>関連項目  
 [プロジェクトの既定の Namespace を決定します。](../../misc/determining-the-default-namespace-of-a-project.md)   
 [ビジュアル デザイナーへのタイプの公開](../../extensibility/internals/exposing-types-to-visual-designers.md)

