---
title: レガシ API を使用してビューの設定を変更する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - changing view settings
ms.assetid: 12c9b300-0894-4124-96a1-764326176d77
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9857daab890c2dd7bf7a799b6dca4d1b74cb9e37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="changing-view-settings-by-using-the-legacy-api"></a>レガシ API を使用してビューの設定を変更します。
ワード ラップ、マージン、および仮想の領域などのコア エディター機能の設定は、のユーザーによって変更できます、**オプション** ダイアログ ボックス。 ただし、これらの設定を変更することはもプログラムでします。  
  
## <a name="changing-settings-by-using-the-legacy-api"></a>レガシ API を使用して設定を変更します。  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>インターフェイスは、一連のテキスト エディターのプロパティを公開します。 テキスト ビューには、テキスト ビューの変更をプログラムで設定のグループを表すプロパティ (GUID_EditPropCategory_View_MasterSettings) のカテゴリが含まれています。 ビューの設定は、この方法で変更されたが後で変更できません、**オプション**リセットされるまで ダイアログ ボックス。  
  
 コア エディターのインスタンスの表示設定を変更するための一般的なプロセスを次に示します。  
  
1.  呼び出す`QueryInterface`上、(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>) の<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>インターフェイスです。  
  
2.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A>の GUID_EditPropCategory_View_MasterSettings の値を指定して、メソッド、`rguidCategory`パラメーター。  
  
     ポインターを返しますこれを行う、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer>インターフェイスで、ビューの強制のプロパティのセットが含まれています。 このグループ内のすべての設定を完全に求められます。 設定は、このグループに含まれないかどうかで指定されたオプションに従います、**オプション** ダイアログ ボックスまたはユーザーのコマンド。  
  
3.  呼び出す、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>で適切な設定値を指定して、メソッド、`idprop`パラメーター。  
  
     たとえば、右端で折り返すには、呼び出す<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>VSEDITPROPID_ViewLangOpt_WordWrap の値を指定して`vt`の`idprop`パラメーター。 この呼び出しで`vt`型 VT_BOOL のバリアントと`vt.boolVal`は VARIANT_TRUE です。  
  
## <a name="resetting-changed-view-settings"></a>変更されたビューの設定をリセットします。  
 コア エディターのインスタンスの設定の変更された任意のビューをリセットするには、呼び出し、<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>メソッドで適切な設定値を指定し、`idprop`パラメーター。  
  
 たとえば、自由にフローティングするワード ラップを許可するのにはから削除するプロパティのカテゴリを呼び出して<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.RemoveProperty%2A>の VSEDITPROPID_ViewLangOpt_WordWrap の値を指定して、`idprop`パラメーター。  
  
 コア エディターの設定が変更されたすべてを一度に削除する VSEDITPROPID_ViewComposite_AllCodeWindowDefaults の vt の値を指定、`idprop`パラメーター。 この呼び出しで vt 型 VT_BOOL のバリアント、vt.boolVal VARIANT_TRUE です。  
  
## <a name="see-also"></a>関連項目  
 [コア エディター内](../extensibility/inside-the-core-editor.md)   
 [レガシ API を使用してテキスト ビューにアクセスします。](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)   
 [[オプション] ダイアログ ボックス](../ide/reference/options-dialog-box-visual-studio.md)