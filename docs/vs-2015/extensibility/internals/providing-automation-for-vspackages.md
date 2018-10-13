---
title: オートメーション Vspackage の提供 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c527d34abcd8743cd8a521acc6ee372ae04eee6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49210419"
---
# <a name="providing-automation-for-vspackages"></a>VSPackage でのオートメーションの提供
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

自動化、Vspackage 用に提供する 2 つの主な方法があります: VSPackage に固有のオブジェクトを実装することで、標準的なオートメーション オブジェクトを実装することで。 一般に、これらを併用する環境のオートメーション モデルを拡張します。  
  
## <a name="vspackage-specific-objects"></a>VSPackage に固有のオブジェクト  
 オートメーション モデル内の特定の場所では、VSPackage に固有のオートメーション オブジェクトを提供する必要があります。 たとえば、新しいプロジェクトには、VSPackage のみを提供する個別のオブジェクトが必要です。 これらのオブジェクトの名前がレジストリに登録し、環境への呼び出し経由で取得した`DTE`オブジェクト。  
  
 Automation、コンシューマーが標準オブジェクトのオブジェクトのプロパティで指定されたオブジェクトを使用する場合、VSPackage に固有のオブジェクトを取得することもできます。 たとえば、標準的な`Window`オブジェクトには、`Object`とよく呼ばれるプロパティ、`Windows.Object`プロパティ。 コンシューマーを呼び出すときに、`Window.Object`バックアップに渡す VSPackage に実装されているウィンドウで、独自の設計の特定のオートメーション オブジェクト。  
  
#### <a name="projects"></a>プロジェクト  
 Vspackage では、独自の VSPackage に固有のオブジェクトから新しいプロジェクトの種類のオートメーション モデルを拡張できます。 VSPackage が、一意のプロジェクトを区別するためには、新しいオートメーション オブジェクトを提供することの主な目的のオブジェクトから、<xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>または<xref:VSLangProj80.VSProject2>オブジェクト。 この違いは、サイド バイ サイドでを表示する必要があります 1 つまたはその他のプロジェクトの種類とは別のプロジェクトの種類を反復処理する方法を提供する場合に便利なソリューションです。 詳細については、次を参照してください。[プロジェクト オブジェクトを公開する](../../extensibility/internals/exposing-project-objects.md)します。  
  
#### <a name="events"></a>イベント  
 環境のイベントのアーキテクチャでは、独自の VSPackage に固有のオブジェクトを追加するための別の場所を提供します。 たとえば、独自の一意のイベント オブジェクトを作成すると、プロジェクトの環境のイベント モデルを拡張できます。 新しい項目が独自のプロジェクトの種類に追加されたときに、独自のイベントを提供する可能性があります。 詳細については、次を参照してください。[イベントを公開する](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)します。  
  
#### <a name="window-objects"></a>ウィンドウ オブジェクト  
 Windows 返すことができる VSPackage に固有のオートメーション オブジェクトが呼び出されたときに、環境にします。 派生したオブジェクトを実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>、<xref:EnvDTE.IExtensibleObject>または`IDispatch`が配置されてウィンドウ オブジェクトの拡張プロパティに戻るを渡します。 たとえば、ウィンドウ フレームに配置されたコントロールの自動化に提供するのにこの方法を使用できます。 このオブジェクトとそれが長引く可能性があるその他のオブジェクトのセマンティクスは、皆さんの仕事が設計です。 詳細については、次を参照してください。[方法: Windows のオートメーションの提供](../../extensibility/internals/how-to-provide-automation-for-windows.md)します。  
  
#### <a name="options-pages-on-the-tools-menu"></a>ツール メニュー オプション ページ  
 ツール、ページを実装すると、独自のオプションを作成するレジストリ情報を追加するオプションのオートメーション モデルを拡張するページを作成することができます。 ページは、他のオプション ページのように、環境のオブジェクト モデルを通じて呼び出すことができます。 Vspackage を環境に追加する機能の設計には、[オプション] ページが必要とする場合は、オートメーションのサポートを追加する必要があります。 詳細については、次を参照してください。[オートメーションのサポート オプション ページ](../../extensibility/internals/automation-support-for-options-pages.md)します。  
  
## <a name="standard-automation-objects"></a>標準的なオートメーション オブジェクト  
 標準的なオートメーション オブジェクトの実装もプロジェクトの自動化を拡張する (から派生した`IDispatch`) をプロジェクトの他のオブジェクトの横にあるスタンドアロンし、標準的なメソッドとプロパティを実装します。 標準オブジェクトのものがプロジェクト オブジェクトなど、ソリューションの階層に挿入された`Projects`、 `Project`、 `ProjectItem`、および`ProjectItems`します。 新しい各プロジェクトの種類には、これらのオブジェクト (と可能性があります、プロジェクトのセマンティクスに応じて他の) を実装する必要があります。  
  
 ある意味では、これらのオブジェクトは、VSPackage に固有のプロジェクトのオブジェクトの逆の利点を提供します。 標準的なオートメーション オブジェクトは、同じオブジェクトをサポートしている他のプロジェクトなどの一般的な方法で使用するプロジェクトを使用します。 そのため、アドインを [全般] に対して記述された`Project`と`ProjectItem`オブジェクトが任意の種類のプロジェクトに対して機能します。 詳細については、次を参照してください。[プロジェクトのモデリング](../../extensibility/internals/project-modeling.md)します。

