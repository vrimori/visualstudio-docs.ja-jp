---
title: "従来の言語サービスのクイック ヒント | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "クイック ヒント、言語サービス [マネージ パッケージ フレームワーク] でのサポート"
  - "IntelliSense、クイック ヒント"
  - "言語サービス [マネージ パッケージ フレームワーク] intellisense によるクイック ヒント"
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# 従来の言語サービスのクイック ヒント
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ユーザーが、識別子、キャレットを配置し、選択時に、intellisense によるクイック ヒントで、ソースで、識別子に関する情報が表示 **クイック ヒント** から、 **IntelliSense** メニューまたは識別子の上にマウス カーソルを保持します。 これにより、識別子に関する情報を表示するツールヒント。 この情報は、通常、識別子の型で構成されています。 デバッグ エンジンがアクティブである場合、この情報は、現在の値を含めることがあります。 デバッグ エンジンは、言語サービスは、識別子だけを処理中に、式の値を提供します。  
  
 従来の言語サービスは、VSPackage の一部として実装されますが、言語サービスの機能を実装する新しい方法は、MEF の拡張機能を使用します。 詳細については、次を参照してください。 [チュートリアル: クイック ヒントの表示](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md)します。  
  
> [!NOTE]
>  エディターを使用して、新しい API できるだけ早く始めることをお勧めします。 言語サービスのパフォーマンスを向上させる、エディターの新機能を活用できます。  
  
 マネージ パッケージ フレームワーク \(MPF\) 言語のサービス クラスは、intellisense によるクイック ヒントのツールヒントを表示するため、完全にサポートを提供します。 行う必要があるすべては表示されず、クイック ヒント機能を有効にするテキストを指定します。  
  
 呼び出すことによって表示されるテキストを取得、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> パーサーの解析理由値ではメソッド <xref:Microsoft.VisualStudio.Package.ParseReason>します。 この理由から型情報 \(または、クイック ツールヒントに表示するには、適切な処理\) を取得するパーサーに伝える識別子で指定された位置の <xref:Microsoft.VisualStudio.Package.ParseRequest> オブジェクトです。<xref:Microsoft.VisualStudio.Package.ParseRequest> に何が渡されたオブジェクトは、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドです。  
  
 パーサーは内の位置までのすべてを解析する必要があります、 <xref:Microsoft.VisualStudio.Package.ParseRequest> オブジェクトのすべての識別子の種類を決定するためにします。 パーサーでは、解析要求の場所に識別子を取得する必要があります。 最後に、パーサーはその id に関連付けられているツール ヒントのデータを渡す必要があります、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> オブジェクトのオブジェクトからテキストを返すことができますので、 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> メソッドです。  
  
## クイック ヒント機能を有効にします。  
 クイック ヒント機能を有効に設定すると、 `CodeSense` と `QuickInfo` 名前付きのパラメーター、 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>です。これらの属性を設定、 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> と <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> プロパティです。  
  
## クイック ヒント機能を実装します。  
 <xref:Microsoft.VisualStudio.Package.ViewFilter> クラスは、intellisense によるクイック ヒントの操作を処理します。 ときに、 <xref:Microsoft.VisualStudio.Package.ViewFilter> クラスを受け取る、 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> のコマンドは、クラスの呼び出し、 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 解析理由が付いているメソッド <xref:Microsoft.VisualStudio.Package.ParseReason> と時のキャレットの場所、 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> コマンドが送信されました。<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッド パーサー必要がありますし、指定した位置までソースを解析およびクイック ツールヒントに表示を決定するように指定された場所に識別子を解析します。  
  
 ほとんどのパーサーでは、全体のソース ファイルの初期の解析を行うし、結果を解析ツリーに格納します。 完全な解析を実施タイミング <xref:Microsoft.VisualStudio.Package.ParseReason> に渡される <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> メソッドです。 その他の種類の解析は、必要な情報を取得するのに解析ツリーを使用できます。  
  
 たとえば、解析理由の値の <xref:Microsoft.VisualStudio.Package.ParseReason> ソースの場所にある識別子を確認して、型情報を取得する解析ツリー内を検索します。 この種類の情報に渡されます、 <xref:Microsoft.VisualStudio.Package.AuthoringScope> クラス、およびによって返される、 <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> メソッドです。