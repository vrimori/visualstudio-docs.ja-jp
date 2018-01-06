---
title: "プロジェクトのファクトリを使用してプロジェクトのインスタンスを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project factories
- projects [Visual Studio SDK], project factories
ms.assetid: 94c90012-8669-459c-af8e-307ac242c8c4
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 8a331c131eaf48eb7be8bc3709599412aa01b1ca
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="creating-project-instances-by-using-project-factories"></a>プロジェクトのファクトリを使用してプロジェクトのインスタンスを作成します。
プロジェクトの種類に[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]を使用して、*プロジェクト ファクトリ*プロジェクトのオブジェクトのインスタンスを作成します。 プロジェクト ファクトリは、cocreatable の COM オブジェクトの標準のクラス ファクトリに似ています。 ただし、プロジェクトのオブジェクトは、cocreatable: プロジェクト ファクトリを使用してのみ作成します。  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE は、ユーザーが既存のプロジェクトをロードまたはで新しいプロジェクトを作成するときに、VSPackage の実装プロジェクト ファクトリを呼び出す[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]です。 新しいプロジェクトのオブジェクトは、ソリューション エクスプ ローラーを設定するための十分な情報を使用して IDE を提供します。 新しいプロジェクトのオブジェクトでは、IDE によって開始されたすべての関連する UI 操作をサポートするため、必要なインターフェイスも提供します。  
  
 実装することができます、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>プロジェクト内のクラスのインターフェイスです。 通常、独自のモジュールに存在します。  
  
 実装の例については、`IVsProjectFactory`インターフェイスに含まれている PrjFac.cpp を参照してください、[基本的なプロジェクト](http://msdn.microsoft.com/en-us/385fd2a3-d9f1-4808-87c2-a3f05a91fc36)サンプル ディレクトリ。  
  
 所有者によって集計されるをサポートするプロジェクトには、そのプロジェクト ファイルで、所有者キーが永続化する必要があります。 ときに、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>所有者キーを使用して、プロジェクトでメソッドは、所有されているプロジェクトは、その所有者のキーを GUID を呼び出してプロジェクト ファクトリに変換します、`CreateProject`を実際の作成を行うには、このプロジェクト ファクトリ メソッド。  
  
## <a name="creating-an-owned-project"></a>所有されているプロジェクトを作成します。  
 所有者は、2 つのフェーズに所有されているプロジェクトを作成します。  
  
1.  呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.PreCreateForOwner%2A>メソッドです。 これは、方法により所有されているプロジェクト入力の制御に基づく集計プロジェクト オブジェクトを作成する`IUnknown`です。 所有されているプロジェクト渡します内部`IUnknown`と所有者のプロジェクトに集計されたオブジェクト。 これは、方法により所有されているプロジェクトを内部に格納する`IUnknown`です。  
  
2.  呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>メソッドです。 呼び出す代わりにこのメソッドが呼び出されたときに、所有されているプロジェクトは、すべてのインスタンス生成`IVsProjectFactory::CreateProject`が所有していないプロジェクトの場合と同様です。 入力`VSOWNEDPROJECTOBJECT`列挙体は、通常、集計の所有されているプロジェクト。 所有されているプロジェクトは、そのプロジェクトのオブジェクトが既に作成されているかどうかを決定するこの変数を使用できます (cookie は NULL は等しくない) か、(cookie 等しい NULL) を作成する必要があります。  
  
 プロジェクトの種類は、一意のプロジェクト GUID、cocreatable COM オブジェクトの CLSID に似ていますによって識別されます。 通常、1 つのプロジェクト ファクトリを設定することが、1 つのプロジェクトの種類のインスタンスを作成する 1 つのプロジェクト ファクトリ ハンドルは、1 つ以上のプロジェクトの種類の GUID を処理します。  
  
 プロジェクトの種類は、特定のファイル名拡張子に関連付けられます。 ユーザーは、既存のプロジェクト ファイルを開こうとしたか、テンプレートを複製して新しいプロジェクトを作成しようとしています、IDE、拡張子を使用してファイルに対応するプロジェクトの GUID を決定します。  
  
 IDE では、IDE が、かを調べる [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\8.0\Projects] の下のシステム レジストリの情報を使用して新しいプロジェクトを作成するか、特定の種類の既存のプロジェクトを開く必要があります、かどうかを判断するとすぐにVSPackage では、必要なプロジェクト ファクトリを実装します。 IDE には、この VSPackage が読み込まれます。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>メソッド、VSPackage は呼び出すことにより、IDE を使用してそのプロジェクト ファクトリを登録する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes.RegisterProjectType%2A>メソッドです。  
  
 主な方法、`IVsProjectFactory`インターフェイスは<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>2 つのシナリオを処理する必要があります: 既存のプロジェクトを開き、新しいプロジェクトを作成します。 ほとんどのプロジェクトでは、プロジェクト ファイル内のプロジェクト状態を格納します。 渡されるテンプレート ファイルのコピーすることで新しいプロジェクトを作成する通常、`CreateProject`メソッドおよびコピーします。 直接に渡されるプロジェクト ファイルを開き、既存のプロジェクトはによってインスタンス化`CreateProject`メソッドです。 `CreateProject`メソッドは、必要に応じて、ユーザーに追加の UI 機能を表示できます。  
  
 プロジェクトは、ファイルも使用しないでき、代わりに、データベースや Web サーバーなど、ファイル システム以外のストレージ メカニズムにそのプロジェクトの状態を格納できます。 この例では、ファイル名のパラメーターが渡される、`CreateProject`メソッドではありませんが、ファイル システム パスを実際には、一意の文字列-URL: プロジェクト データを識別します。 渡されるテンプレート ファイルをコピーする必要はありません`CreateProject`を実行する適切な構築シーケンスをトリガーします。  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterProjectTypes>   
 [チェック リスト: 新しいプロジェクト タイプの作成](../../extensibility/internals/checklist-creating-new-project-types.md)