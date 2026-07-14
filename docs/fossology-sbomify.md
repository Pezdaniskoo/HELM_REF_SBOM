# FOSSology and sbomify in the Helm SPDX Workflow

## Purpose

The Helm workflow is SPDX-focused. Its review and tracking stage is centered on license compliance and SBOM decision history, not vulnerability scanning.

## FOSSology

FOSSology is represented as the license compliance review tool.

The workflow prepares SPDX SBOM artifacts that can be imported into FOSSology for manual or centralized review. It does not automatically upload to FOSSology because that requires a configured FOSSology server and API credentials.

Expected input files:

- `sbom/helm/source/helm.source.syft.spdx.json`
- `sbom/helm/artifacts/helm.artifacts.syft.spdx.json`

The workflow records this stage under:

- `review-results/helm/fossology/fossology-review-status.md`
- `review-results/helm/fossology/fossology-review-status.json`

## sbomify

sbomify is included as an optional SBOM storage/tracking integration.

The workflow checks for these secrets:

- `SBOMIFY_TOKEN`
- `SBOMIFY_COMPONENT_ID`

If they are missing, the upload is skipped and a status file is written. If they are present, the workflow records that the integration is configured, but the final upload endpoint can be adapted to the target sbomify setup.

The workflow records this stage under:

- `review-results/helm/sbomify/sbomify-upload.log`
- `review-results/helm/sbomify/sbomify-status.json`