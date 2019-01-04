---
title: カスタム ツール |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, custom tools
- tools [Visual Studio], custom
- custom tools
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ce8b18ee5c1c84b8e6480ffa9f91f739796f0991
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834413"
---
# <a name="custom-tools"></a>カスタム ツール
*カスタム ツール*ツールをプロジェクト内の項目に関連付けるし、ファイルを保存するたびに、そのツールを実行することができます。 特定のカスタム ツールとも呼ば*単一ファイル ジェネレーター*、データから、またはその逆にコードを生成する翻訳者を実装するために頻繁に使用されます。 たとえば、単一ファイル ジェネレーターの作成[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]ソース コードのうち、 *.settings*と *.resx*ファイル。 生成されたソース コード内のデータに厳密に型指定されたアクセスを提供する、 *.settings*と *.resx*ファイル。 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]と[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]; のカスタム ツールをサポートするプロジェクトの種類[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]プロジェクトの種類はありません。 独自のプロジェクトの種類には、カスタム ツールもサポートできます。  
  
 カスタム ツールを実装するコンポーネントが登録されているは、`IVsSingleFileGenerator`インターフェイス。  
  
 カスタム ツールの関連付けられている、`ProjectItem`インターフェイス オブジェクト、およびデザイナーおよびエディターのようなものです。 カスタム ツールで表されるファイルでは、`ProjectItem`入力し、ファイル名がによって提供される新しいファイルを書き込むだけ、`DefaultExtension`メソッド。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [単一ファイル ジェネレーターを実装します。](../../extensibility/internals/implementing-single-file-generators.md)  
 使用する方法について説明します、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>カスタム ツールを実装するインターフェイス。  
  
 [単一ファイル ジェネレーターを登録します。](../../extensibility/internals/registering-single-file-generators.md)  
 カスタム ツールのすべてのレジストリ エントリについて説明します。  
  
 [ビジュアル デザイナーへの型を公開します。](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 どのようにプロジェクト システム サポートを提供アクセスが生成されるクラスと型をビジュアル デザイナーの一時的なポータブル実行可能 (PE) ファイルをについて説明します。  
  
 [プロジェクト項目のプロパティを永続化します。](../../extensibility/persisting-the-property-of-a-project-item.md)  
 プロジェクト ファイル内のソース ファイルの作成者など、プロジェクト項目のプロパティを永続化する方法を示しています。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 詳細について説明します、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>、1 つの入力ファイルをコンパイルまたはプロジェクトに追加できる単一の出力ファイルに変換します。  
  
 <xref:EnvDTE.ProjectItem>  
 について説明します、`ProjectItem`インターフェイスで、プロジェクト内の項目を表します。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 詳細について説明します、`DefaultExtension`メソッドで、出力ファイル名に指定されているファイル名拡張子を取得します。  
  
## <a name="related-sections"></a>関連項目  
 [プロジェクトを拡張します。](../../extensibility/extending-projects.md)  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] プロジェクトおよびソリューションを使用してコード ファイルとリソース ファイルを編成する方法、またソース管理を実装する方法について説明します。