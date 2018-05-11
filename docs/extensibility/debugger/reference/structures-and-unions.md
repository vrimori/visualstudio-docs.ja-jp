---
title: 構造体と共用体 |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 33e3f5ebb4e871f98b027638f5aae47d853828a8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="structures-and-unions"></a>構造体と共用体
構造体と Visual Studio Debugging SDK の共用体は次のとおりです。  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 プロセス ID は、システム ID または GUID のいずれかである可能性がありますを指定します。  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 ブレークポイントが発生する条件をについて説明します。  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 場所、プログラム、スレッドなど、エラー ブレークポイントの解決について説明します。  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 ブレークポイントの位置を指す構造体の型を指定します。  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 コード内のアドレスのブレークポイントの場所を記述するコンポーネントを定義します。  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 デバッグ中のプログラム内のアドレスに直接バインドされているブレークポイントの場所について説明します。  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 コードのソース ファイル内の行のブレークポイントの場所について説明します。  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 コード内の関数のブレークポイントのオフセットの位置をについて説明します。  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 ユーザーは、IDE から入力文字列に基づくコードのブレークポイントを設定するために使用します。  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 ユーザーは、IDE から入力を文字列に基づくデータ ブレークポイントを設定するために使用します。  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 特定の場所のブレークポイントの解決について説明します。  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 既に通過した後に発生するブレークポイントを基になる、カウントと条件について説明します。  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 ブレークポイントの実装に必要な情報が含まれています。  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 ブレークポイントの実装に必要な情報が含まれています (と同じ、 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)構造体には、ベンダーの GUID、制約、およびトレース ポイントの情報が含まれています)。  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 コードのブレークポイントの場所について説明します。  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 データ ブレークポイントのバインドの結果について説明します。  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 コードのブレークポイントまたはデータ ブレークポイントのいずれかのバインドされたブレークポイント情報について説明します。  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 ブレークポイントの解像度の場所の構造を指定します。  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 文字列の配列について説明します。  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 メタデータから取得されたフィールドの種類に関する情報を指定します。  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 関数またはメソッドへの呼び出しについて説明します。  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 デバッガーが実行されているコンピューターをについて説明します。  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Guid のリストについて説明します。  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 メモリ コンテキストまたはコードのコンテキストについて説明します。  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 デバッグ中のプログラムでアドレスについて説明します。  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 アドレスのさまざまな種類の数のいずれかを表します。  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 カスタム ビューアーの識別またはビジュアライザーを入力します。  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 さらにオブジェクトを表すを名前、型、および値を持つ階層的な性質のデバッグ プロパティについて説明します。  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 参照を記述します。  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 表示するための IDE に逆アセンブルをについて説明します。  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 例外またはデバッグ中のプログラムによってスローされた実行時エラーについて説明します。  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 ローカル変数、パラメーター、またはその他のフィールドについて説明します。  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 スタック フレームを説明します。  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 使用可能なデバッグ エンジンの一意の識別子の配列について説明します。  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 モジュールの JustMyCode 情報を設定するために使用します。  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 特定のコンピューターについて説明します。  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 配列内の配列要素をについて説明します。  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 クラスまたは構造体のフィールドのアドレスをについて説明します。  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 (通常の関数またはメソッド) のスコープ内でローカル変数のアドレスをについて説明します。  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 クラスのメソッドのアドレスをについて説明します。  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 メソッドまたは関数のパラメーターについて説明します。  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 メソッドまたは関数からの戻り値をについて説明します。  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 メタデータから取得されたフィールドの種類について説明します。  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 特定のモジュール (DLL、exe ファイルまたはアセンブリ) について説明します。  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 検索したシンボル検索パスに関する状態情報をについて説明します。  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 ネイティブのアドレスをについて説明します。  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 PDB シンボルから取得したフィールドの種類について説明します。  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 コードの場所にバインドする準備が整っているブレークポイントの状態について説明します。  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 プロセスをについて説明します。  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 説明の一覧[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)プログラム ノードを表すオブジェクト。  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 コンピューターで実行中のプロセスについて説明します。  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 指定されたテキストで行と列の場所について説明します。  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 スレッドのプロパティについて説明します。  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 フィールドの型について説明します。  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 物理アドレスをについて説明します。  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 基準には、アドレスの説明、`this`ポインター (`Me` Visual Basic で)。  
  
## <a name="requirements"></a>要件  
 ヘッダー: msdbg.h、sh.h、または ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>関連項目  
 [API リファレンス](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)