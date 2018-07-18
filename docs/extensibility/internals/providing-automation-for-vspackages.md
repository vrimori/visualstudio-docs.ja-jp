---
title: Vspackage の自動化を提供する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, automation [Visual Studio SDK]
- automation [Visual Studio SDK], VSPackages
ms.assetid: 104c4c55-78b8-42f4-b6b0-9a334101aaea
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fb5f3393443e41c9bd99a8890b53bedae006d7a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131581"
---
# <a name="providing-automation-for-vspackages"></a>Vspackage の自動化を提供します。
Vspackage の自動化を提供する 2 つの主な方法があります: VSPackage に固有のオブジェクトを実装することで、標準のオートメーション オブジェクトを実装することによってです。 一般に、これらを併用するを環境のオートメーション モデルを拡張します。  
  
## <a name="vspackage-specific-objects"></a>VSPackage に固有のオブジェクト  
 オートメーション モデル内の特定の場所では、VSPackage に固有のオートメーション オブジェクトを指定する必要があります。 たとえば、新しいプロジェクトでは、VSPackage のみを提供する独立したオブジェクトが必要です。 これらのオブジェクトの名前がレジストリに登録し、環境への呼び出しによって取得した`DTE`オブジェクト。  
  
 オートメーション コンシューマーは、標準のオブジェクトのオブジェクト プロパティによって指定されたオブジェクトを使用する場合、VSPackage に固有のオブジェクトを取得することができますも。 たとえば、標準の`Window`オブジェクトには、`Object`プロパティとよく呼ばれる、`Windows.Object`プロパティです。 コンシューマーが呼び出す場合、`Window.Object`バックアップに渡す VSPackage に実装されているウィンドウで、独自の設計の特定のオートメーション オブジェクト。  
  
#### <a name="projects"></a>プロジェクト  
 Vspackage では、独自の VSPackage に固有のオブジェクトから新しいプロジェクトの種類のオートメーション モデルを拡張できます。 VSPackage が、一意のプロジェクトを区別するためには、新しいオートメーション オブジェクトを提供することの主な目的のオブジェクトから、<xref:Microsoft.VisualStudio.VCProjectEngine.VCProject>または<xref:VSLangProj80.VSProject2>オブジェクト。 この違いは、サイド バイ サイドを表示する必要があります 1 つまたはその他のプロジェクトの種類とは別のプロジェクトの種類を反復処理する方法を提供する場合に便利なソリューションです。 詳細については、次を参照してください。[プロジェクト オブジェクトを公開する](../../extensibility/internals/exposing-project-objects.md)です。  
  
#### <a name="events"></a>イベント  
 環境のイベントのアーキテクチャでは、独自の VSPackage に固有のオブジェクトを追加するための別の場所を提供します。 たとえば、独自の一意のイベント オブジェクトを作成すると、プロジェクトの環境のイベント モデルを拡張できます。 新しい項目がプロジェクトの種類に追加されると、独自のイベントを提供する可能性があります。 詳細については、次を参照してください。[イベントを公開する](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)です。  
  
#### <a name="window-objects"></a>ウィンドウ オブジェクト  
 Windows 返すことができる VSPackage に固有のオートメーション オブジェクトが呼び出されたときに、環境に戻す。 派生したオブジェクトを実装する<xref:Microsoft.VisualStudio.Shell.Interop.IVsExtensibleObject>、<xref:EnvDTE.IExtensibleObject>または`IDispatch`が配置されてウィンドウ オブジェクトの拡張プロパティに戻るを渡します。 たとえば、このアプローチを使用すると、ウィンドウ フレームに配置されたコントロールのオートメーションを提供します。 このオブジェクトとそれが長引く可能性があるその他のオブジェクトのセマンティクスは、デザインに自分のものです。 詳細については、次を参照してください。[する方法: Windows 用のオートメーションの提供](../../extensibility/internals/how-to-provide-automation-for-windows.md)です。  
  
#### <a name="options-pages-on-the-tools-menu"></a>ツール メニュー オプション ページ  
 ツール オプション ページを実装して、独自のオプションを作成するためにレジストリに情報を追加することを使用してオートメーション モデルを拡張するページを作成することができます。 ページは、その他のオプション ページのように、環境のオブジェクト モデルを通じて呼び出すことができます。 Vspackage を環境に追加する機能の設計には、[オプション] ページが必要とする場合は、オートメーションのサポートを追加する必要があります。 詳細については、次を参照してください。[オートメーション オプション ページのサポート](../../extensibility/internals/automation-support-for-options-pages.md)です。  
  
## <a name="standard-automation-objects"></a>標準のオートメーション オブジェクト  
 プロジェクトの自動化を拡張するを実装することも標準のオートメーション オブジェクト (から派生した`IDispatch`) を他のプロジェクトのオブジェクトの横にあるスタンドアロンし、標準的なメソッドとプロパティを実装します。 標準的なオブジェクトの例としてなどをソリューション階層に挿入されるプロジェクト オブジェクト`Projects`、 `Project`、 `ProjectItem`、および`ProjectItems`です。 すべて新しいプロジェクトの種類には、これらのオブジェクト (および可能性がありますセマンティクスによって、プロジェクトの他の) を実装する必要があります。  
  
 意味では、これらのオブジェクトは、VSPackage に固有のプロジェクトのオブジェクトの逆の利点を提供します。 標準のオートメーション オブジェクトは、同じオブジェクトをサポートする他のプロジェクトなどの一般的な方法で使用するようにプロジェクトを許可します。 このため、アドインを [全般] に対して記述された`Project`と`ProjectItem`オブジェクトが任意の型のプロジェクトに対して機能します。 詳細については、次を参照してください。[プロジェクトがモデリング](../../extensibility/internals/project-modeling.md)です。