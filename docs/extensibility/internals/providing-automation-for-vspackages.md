---
title: "Vspackage のための自動化を提供する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: ca3700d1e26ccd4be1054463e9426b364ba17301
ms.lasthandoff: 02/22/2017

---
# <a name="providing-automation-for-vspackages"></a>Vspackage のための自動化を提供します。
Vspackage のための自動化を提供する&2; つの主な方法があります: VSPackage に固有のオブジェクトを実装することによって、標準的なオートメーション オブジェクトを実装することで。 一般に、これらを併用、環境のオートメーション モデルを拡張します。  
  
## <a name="vspackage-specific-objects"></a>VSPackage に固有のオブジェクト  
 オートメーション モデル内の特定の場所では、VSPackage に固有のオートメーション オブジェクトを指定する必要があります。 たとえば、新しいプロジェクトは、vs パッケージを提供する個々 のオブジェクトが必要です。 これらのオブジェクトの名前が、レジストリに入力し、環境への呼び出しによって取得した`DTE`オブジェクトです。  
  
 VSPackage に固有のオブジェクトは、オートメーション コンシューマーは、標準的なオブジェクトのオブジェクトのプロパティを介して提供されるオブジェクトを使用する場合にも取得できます。 たとえば、標準の`Window`オブジェクトには、`Object`プロパティとよく呼ばれる、`Windows.Object`プロパティです。 コンシューマーが呼び出す場合、`Window.Object`バックアップに渡す、VSPackage に実装されているウィンドウで、独自に設計の特定のオートメーション オブジェクト。  
  
#### <a name="projects"></a>プロジェクト  
 Vspackage では、独自の VSPackage に固有のオブジェクトから新しいプロジェクトの種類のオートメーション モデルを拡張できます。 VSPackage が一意のプロジェクトを区別するためには、新しいオートメーション オブジェクトを提供することの主な目的のオブジェクトから、<xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>または<xref:VSLangProj80.VSProject2>オブジェクト</xref:VSLangProj80.VSProject2></xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>。 この違いは、サイド バイ サイドを表示する必要があります除外またはその他のプロジェクトの種類とは別のプロジェクトの種類を反復処理する方法を提供する場合に便利なソリューションです。 詳細については、次を参照してください。[プロジェクト オブジェクトを公開する](../../extensibility/internals/exposing-project-objects.md)です。  
  
#### <a name="events"></a>イベント  
 環境のイベントのアーキテクチャでは、独自の VSPackage に固有のオブジェクトを追加するための別の場所を提供します。 たとえば、独自の一意のイベント オブジェクトを作成すると、プロジェクトの環境のイベント モデルを拡張できます。 プロジェクトの種類に新しい項目が追加されると、独自のイベントを提供する可能性があります。 詳細については、次を参照してください。[イベントを公開する](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)です。  
  
#### <a name="window-objects"></a>ウィンドウ オブジェクト  
 Windows 返すことができる VSPackage に固有のオートメーション オブジェクトを呼び出したときに環境に戻す。 派生したオブジェクトを実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>、<xref:EnvDTE.IExtensibleObject>または`IDispatch`が配置されてウィンドウ オブジェクトの拡張プロパティで渡す戻します</xref:EnvDTE.IExtensibleObject></xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>。 たとえば、このアプローチを使用すると、ウィンドウ フレームに配置されたコントロールの自動化機能を提供します。 このオブジェクトと可能性のあるその他のオブジェクトのセマンティクスは、皆さんの仕事が設計です。 詳細については、次を参照してください。[方法: Windows 用の自動化を提供](../../extensibility/internals/how-to-provide-automation-for-windows.md)します。  
  
#### <a name="options-pages-on-the-tools-menu"></a>ツール メニュー オプション ページ  
 ツールのページを実装すると、独自のオプションを作成するレジストリ情報を追加するオプションのオートメーション モデルを拡張するページを作成することができます。 ページは、その他のオプション ページのような環境オブジェクト モデルを通じて呼び出すことができます。 VSPackages を介して環境に追加する機能の仕様には、[オプション] ページが必要とする場合は、オートメーションのサポートを追加する必要があります。 詳細については、次を参照してください。[オートメーションのサポート オプション ページ](../../extensibility/internals/automation-support-for-options-pages.md)します。  
  
## <a name="standard-automation-objects"></a>標準的なオートメーション オブジェクト  
 標準的なオートメーション オブジェクトの実装もプロジェクトのための自動化を拡張する (から派生した`IDispatch`) を他のプロジェクトのオブジェクトの横にあるスタンドアロンし、標準的なメソッドとプロパティを実装します。 標準的なオブジェクトの例としてはなどソリューション階層構造に挿入されるプロジェクト オブジェクトを含める`Projects`、 `Project`、 `ProjectItem`、および`ProjectItems`です。 新しい各プロジェクトの種類には、これらのオブジェクト (と可能性があります、プロジェクトのセマンティクスによって他の) を実装する必要があります。  
  
 ある意味では、これらのオブジェクトは、VSPackage に固有のプロジェクトのオブジェクトの逆の利点を提供します。 標準的なオートメーション オブジェクトは、同じオブジェクトをサポートする他のプロジェクトのような一般的な方法で使用するようにプロジェクトを使用します。 このため、アドインで一般的なに対して記述された`Project`と`ProjectItem`オブジェクトが任意の種類のプロジェクトに対して機能します。 詳細については、次を参照してください。[プロジェクトがモデリング](../../extensibility/internals/project-modeling.md)します。
