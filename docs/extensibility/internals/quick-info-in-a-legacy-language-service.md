---
title: 従来の言語サービスで、クイック ヒント |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Quick Info, supporting in language services [managed package framework]
- IntelliSense, Quick Info
- language services [managed package framework], IntelliSense Quick Info
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdfe9bfb9063828a90dd9cdf3452ca3684ff0a5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31132156"
---
# <a name="quick-info-in-a-legacy-language-service"></a>従来の言語サービスで、クイック ヒント
Intellisense によるクイック ヒントでは、ユーザーか、キャレットを配置します id に、選択して、ソースの識別子に関する情報を表示**クイック ヒント**から、 **IntelliSense**メニューまたはマウスを保持識別子の上にカーソル。 これにより、識別子の情報を表示するツールヒント。 この情報は、通常、識別子の型で構成されています。 デバッグ エンジンがアクティブで、この情報は、現在の値を含めることがあります。 デバッグ エンジンは、言語サービスは識別子のみを処理中に、式の値を指定します。  
  
 レガシ言語サービスは、VSPackage の一部として実装されますが、MEF 拡張機能を使用する言語サービスの機能を実装する新しい方法です。 詳細については、次を参照してください。[チュートリアル: クイック ツールヒントを表示する](../../extensibility/walkthrough-displaying-quickinfo-tooltips.md)です。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く開始することをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
 マネージ パッケージ フレームワーク (MPF) 言語サービス クラスは、intellisense によるクイック ヒントのツールヒントを表示するためのサポートを提供します。 行う必要があるすべてが表示され、クイック ヒント機能を有効にするテキストを指定します。  
  
 呼び出すことによって表示されるテキストを取得、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>解析理由値を持つメソッド パーサー<xref:Microsoft.VisualStudio.Package.ParseReason>です。 このため、型情報 (またはクイック ツールヒントに表示するには、適切な処理) を取得するためにパーサーに指示識別子で指定された位置の<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクト。 <xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクトに渡されたもの、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドです。  
  
 パーサーは内の位置までのすべてのものを解析する必要があります、<xref:Microsoft.VisualStudio.Package.ParseRequest>オブジェクトのすべての識別子の種類を決定するためにします。 パーサーは解析要求の場所に識別子を取得する必要があります。 最後に、パーサーは、ツール ヒントのデータをその id に関連付けられたを渡す必要があります、<xref:Microsoft.VisualStudio.Package.AuthoringScope>オブジェクトのため、そのオブジェクトからテキストを返すことができます、<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>メソッドです。  
  
## <a name="enabling-the-quick-info-feature"></a>クイック ヒント機能を有効にします。  
 クイック ヒント機能を有効に設定すると、`CodeSense`と`QuickInfo`名前付きのパラメーター、<xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>です。これらの属性を設定、<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A>と<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A>プロパティです。  
  
## <a name="implementing-the-quick-info-feature"></a>クイック ヒント機能を実装します。  
 <xref:Microsoft.VisualStudio.Package.ViewFilter>クラスは、intellisense によるクイック ヒントの操作を処理します。 ときに、<xref:Microsoft.VisualStudio.Package.ViewFilter>クラスを受け取る、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>のコマンドは、クラスの呼び出し、<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>解析理由をつけてメソッド<xref:Microsoft.VisualStudio.Package.ParseReason>と時に、そのキャレットの場所、<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>コマンドが送信されました。 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッド パーサーが最大で指定された場所のソースを解析してとクイック ツールヒントに表示を決定するように指定された場所に識別子を解析する必要があります。  
  
 ほとんどのパーサーは、全体のソース ファイルの初期の解析を行うし、結果を解析ツリーに格納します。 完全な解析は実行時に<xref:Microsoft.VisualStudio.Package.ParseReason>に渡される<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>メソッドです。 その他の種類の解析は、必要な情報を取得するのに解析ツリーを使用できます。  
  
 たとえば、解析理由の値の<xref:Microsoft.VisualStudio.Package.ParseReason>ソースの場所にある識別子を検索でき、型情報を取得する解析ツリーで検索します。 この型情報に渡され、<xref:Microsoft.VisualStudio.Package.AuthoringScope>クラス、および、によって返される、<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A>メソッドです。